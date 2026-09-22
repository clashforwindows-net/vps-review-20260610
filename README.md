# VPS 证书与密钥管理实战：ACME·TLS·mTLS·GPG

> 证书过期一秒钟，站点就掉线；私钥泄露一次，身份即失守。本文把 VPS 上的**证书生命周期**与**密钥管理**讲透：ACME 自动化签发与续期、通配符证书、mTLS 双向认证、SSH CA、GPG 验签与文件加密、密钥轮换与备份，附可直接复制的命令与配置。

## 目录

- [一、证书与密钥：先建立正确心智模型](#一证书与密钥先建立正确心智模型)
- [二、ACME 与 Let's Encrypt 自动化](#二acme-与-letsencrypt-自动化)
- [三、通配符证书与 DNS-01](#三通配符证书与-dns-01)
- [四、Nginx / Caddy 证书配置](#四nginx--caddy-证书配置)
- [五、证书续期、监控与吊销](#五证书续期监控与吊销)
- [六、mTLS 双向认证](#六mtls-双向认证)
- [七、SSH CA 与主机密钥管理](#七ssh-ca-与主机密钥管理)
- [八、GPG：签名、加密与验签](#八gpg签名加密与验签)
- [九、密钥与机密的安全存取](#九密钥与机密的安全存取)
- [十、轮换、备份与灾难恢复](#十轮换备份与灾难恢复)
- [十一、常见故障与排查](#十一常见故障与排查)
- [十二、FAQ](#十二faq)
- [十三、相关资源](#十三相关资源)

---

## 一、证书与密钥：先建立正确心智模型

- **私钥（Private Key）**：绝不能离开你掌控的机器，泄露即身份被冒用。
- **公钥（Public Key）**：可以公开分发。
- **证书（Certificate）**：由 CA 用其私钥对「你的公钥 + 身份信息」的签名，证明「这把公钥属于这个域名」。
- **CA（证书颁发机构）**：被浏览器/系统信任的第三方。Let's Encrypt 免费提供 DV 证书。

一句话：**TLS 证书解决「你是不是你声称的那个站点」，mTLS 解决「双方是否都可信」，GPG 解决「内容是否被篡改、是否你签的」。**

> 这些机制都跑在服务器上，证书链、私钥、CA 一旦丢失或过期，服务直接不可用。把证书服务放在一台**线路稳定、长期在线**的 VPS 上更省心，例如 [VPSVIP](https://vpsvip.net) 的优化线路很适合做证书签发与内网网关。

---

## 二、ACME 与 Let's Encrypt 自动化

### 2.1 原理

ACME 协议的核心是「证明你控制这个域名」：

- **HTTP-01**：CA 访问 `http://域名/.well-known/acme-challenge/xxx`，需 80 端口可达。
- **DNS-01**：你在 DNS 里加一条 TXT 记录，可签发**通配符**证书，且不要求 80 端口开放。
- **TLS-ALPN-01**：走 443 端口的特殊握手。

### 2.2 用 certbot 签第一张证书

```bash
sudo apt install -y certbot python3-certbot-nginx

# Nginx 一键签发 + 自动改配置
sudo certbot --nginx -d example.com -d www.example.com

# 仅签发不碰 Web 配置
sudo certbot certonly --webroot -w /var/www/html -d example.com

# 测试（不消耗签发配额）
sudo certbot --nginx --dry-run -d example.com
```

证书默认在 `/etc/letsencrypt/live/example.com/`：

| 文件 | 用途 |
|------|------|
| `fullchain.pem` | 服务器证书链（Web 配置用这个） |
| `privkey.pem` | 私钥 |
| `chain.pem` | 中间证书 |
| `cert.pem` | 仅服务器证书 |

### 2.3 自动续期

```bash
# 查看续期定时器
systemctl list-timers | grep certbot
systemctl status certbot.timer

# 手动模拟续期
sudo certbot renew --dry-run
```

**关键**：续期成功后要**重载 Web 服务**。

```ini
# /etc/letsencrypt/renewal-hooks/deploy/reload-nginx.sh
#!/bin/bash
systemctl reload nginx
```

---

## 三、通配符证书与 DNS-01

通配符证书（`*.example.com`）只能走 DNS-01，且需要 DNS API 凭据。

### 3.1 DNS 插件方式（以 Cloudflare 为例）

```bash
sudo apt install -y python3-certbot-dns-cloudflare
```

```ini
# /etc/letsencrypt/cloudflare.ini
dns_cloudflare_api_token = <仅含 DNS 编辑权限的 API Token>
```

```bash
chmod 600 /etc/letsencrypt/cloudflare.ini
sudo certbot certonly \
  --dns-cloudflare \
  --dns-cloudflare-credentials /etc/letsencrypt/cloudflare.ini \
  -d example.com -d '*.example.com'
```

### 3.2 手动 DNS-01（无 API 权限时）

```bash
sudo certbot certonly --manual --preferred-challenges dns -d '*.example.com'
# 按提示在 DNS 添加 _acme-challenge TXT 记录后再回车
```

缺点：需人工介入，无法自动续期。**能用 API 就用 API。**

### 3.3 更现代的替代：acme.sh

```bash
curl https://get.acme.sh | sh -s email=you@example.com
~/.acme.sh/acme.sh --issue --dns dns_cf -d '*.example.com'
~/.acme.sh/acme.sh --install-cert -d '*.example.com' \
  --key-file /etc/nginx/ssl/key.pem \
  --fullchain-file /etc/nginx/ssl/cert.pem \
  --reloadcmd "systemctl reload nginx"
```

acme.sh 自带 100+ DNS 服务商支持，且默认自动装每日续期任务，轻量、无依赖 Python。

---

## 四、Nginx / Caddy 证书配置

### 4.1 Nginx

```nginx
server {
    listen 80;
    server_name example.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl http2;
    server_name example.com;

    ssl_certificate     /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_prefer_server_ciphers on;
    ssl_session_cache shared:SSL:10m;
    ssl_session_timeout 1d;
    ssl_stapling on;
    ssl_stapling_verify on;

    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;

    location / { proxy_pass http://127.0.0.1:3000; }
}
```

### 4.2 Caddy（零配置自动 HTTPS）

```caddyfile
example.com {
    reverse_proxy 127.0.0.1:3000
}
```

Caddy 会自动申请、续期、加载证书，是自托管场景的省心之选。

### 4.3 自签名证书的合理用途

自签只在**内网/开发/测试**使用，别用于公网。

```bash
openssl req -x509 -newkey rsa:4096 -sha256 -days 3650 -nodes \
  -keyout key.pem -out cert.pem \
  -subj "/CN=internal.local" \
  -addext "subjectAltName=DNS:internal.local,IP:10.0.0.5"
```

---

## 五、证书续期、监控与吊销

### 5.1 为什么"自动续期"还会过期

常见原因：

1. 续期任务没跑（服务挂了/被禁）。
2. HTTP-01 失效（80 端口被关、反代没放行 `/.well-known`）。
3. DNS 凭据过期。
4. 域名解析改了，指向了别的机器。

### 5.2 过期监控脚本

```bash
#!/bin/bash
# 检查证书剩余天数，<14 天告警
DOMAINS=(example.com api.example.com)
for d in "${DOMAINS[@]}"; do
  exp=$(echo | openssl s_client -servername "$d" -connect "$d:443" 2>/dev/null \
        | openssl x509 -noout -enddate | cut -d= -f2)
  end=$(date -d "$exp" +%s); now=$(date +%s)
  days=$(( (end - now) / 86400 ))
  echo "$d 剩余 $days 天"
  [ "$days" -lt 14 ] && echo "⚠️ $d 证书即将过期！"
done
```

### 5.3 吊销

私钥泄露必须立刻吊销：

```bash
sudo certbot revoke --cert-path /etc/letsencrypt/live/example.com/cert.pem \
  --reason keycompromise
# 吊销后重新签发
sudo certbot certonly --nginx -d example.com
```

---

## 六、mTLS 双向认证

普通 TLS 只验服务器，mTLS 让**客户端也出示证书**，适合 API 网关、内网服务、设备接入。

### 6.1 用自建 CA 签发客户端证书

```bash
# 1) 建 CA
openssl genrsa -out ca.key 4096
openssl req -x509 -new -nodes -key ca.key -sha256 -days 3650 \
  -subj "/CN=MyInternalCA" -out ca.crt

# 2) 客户端私钥与 CSR
openssl genrsa -out client.key 2048
openssl req -new -key client.key -subj "/CN=client-01" -out client.csr

# 3) CA 签发
openssl x509 -req -in client.csr -CA ca.crt -CAkey ca.key -CAcreateserial \
  -days 825 -sha256 -out client.crt \
  -extfile <(printf "extendedKeyUsage=clientAuth")
```

### 6.2 Nginx 开启 mTLS

```nginx
server {
    listen 443 ssl;
    server_name internal.example.com;

    ssl_certificate     /etc/nginx/ssl/server.crt;
    ssl_certificate_key /etc/nginx/ssl/server.key;

    ssl_client_certificate /etc/nginx/ssl/ca.crt;
    ssl_verify_client on;          # on=强制, optional=可选

    location / {
        proxy_pass http://127.0.0.1:8080;
        proxy_set_header X-Client-DN $ssl_client_s_dn;
    }
}
```

### 6.3 访问测试

```bash
curl --cert client.crt --key client.key --cacert ca.crt \
  https://internal.example.com/
```

### 6.4 mTLS 的运维要点

- 客户端证书也要**有有效期与吊销机制**（CRL / OCSP）。
- 用 CA 统一签发，别逐台手工生成。
- 结合 K8s Ingress / Envoy / Traefik 可自动化。

---

## 七、SSH CA 与主机密钥管理

管理几十台机器时，逐个往 `authorized_keys` 塞公钥会失控。**SSH CA** 一次配置，全员统一。

### 7.1 建立 SSH 用户 CA

```bash
# 在受控的 CA 机器上
ssh-keygen -t ed25519 -f user_ca -C "user-ca"
ssh-keygen -t ed25519 -f host_ca -C "host-ca"
```

### 7.2 服务端信任 CA

```ini
# /etc/ssh/sshd_config
TrustedUserCAKeys /etc/ssh/user_ca.pub
```

```bash
sudo systemctl restart sshd
```

### 7.3 为用户签发短期证书

```bash
ssh-keygen -s user_ca -I "alice@2026-09" -n alice,root \
  -V +8h ~/.ssh/id_ed25519.pub
```

**价值**：证书自带有效期与身份（Principal），过期自动失效，无需去每台机器删公钥。

### 7.4 主机密钥校验

```ini
# 客户端 /etc/ssh/ssh_known_hosts 或 ~/.ssh/known_hosts 中信任 CA
@cert-authority *.example.com ssh-ed25519 AAAA... host_ca.pub
```

这样主机密钥轮换也不用逐个更新 `known_hosts`。

---

## 八、GPG：签名、加密与验签

GPG 用于**代码/发布物签名**、**文件加密**、**邮件加密**。

### 8.1 生成密钥

```bash
gpg --full-generate-key
# 选 (1) RSA and RSA 或 (9) ECC，有效期建议 2 年
gpg --list-secret-keys --keyid-format=long
```

### 8.2 签名与验签

```bash
gpg --armor --detach-sign release.tar.gz       # 生成 release.tar.gz.asc
gpg --verify release.tar.gz.asc release.tar.gz # 验签
gpg --clearsign message.txt                    # 明文签名
```

### 8.3 加密解密

```bash
gpg --encrypt --recipient you@example.com secret.txt   # 生成 secret.txt.gpg
gpg --decrypt secret.txt.gpg > secret.txt
```

### 8.4 对称加密（无对方公钥时）

```bash
gpg --symmetric --cipher-algo AES256 backup.sql
gpg --decrypt backup.sql.gpg > backup.sql
```

### 8.5 用 GPG 给 Git 提交签名

```bash
git config --global user.signingkey <KEYID>
git config --global commit.gpgsign true
git commit -S -m "signed commit"
```

> 发布软件时提供 `.asc` 签名文件，让用户 `gpg --verify`，是防篡改的基本要求。

---

## 九、密钥与机密的安全存取

### 9.1 私钥文件权限

```bash
chmod 600 private.key
chown root:root private.key
```

### 9.2 绝不进版本库

```bash
# .gitignore
*.pem
*.key
.env
*.p12
```

提交前用 `git-secrets` / `gitleaks` 扫描历史，避免误传。

### 9.3 机密管理方案

| 方案 | 适用规模 |
|------|----------|
| 环境变量 + `.env`（600） | 单机小项目 |
| systemd `EnvironmentFile` | 系统服务 |
| Docker secrets / Compose secrets | 容器 |
| HashiCorp Vault | 多服务、需审计与动态凭据 |
| SOPS + age/GPG | Git 里安全存配置 |

**SOPS 典型用法**：

```bash
sops -e -i secrets.yaml    # 加密
sops -d secrets.yaml       # 解密查看/使用
```

加密后的文件可以安全进 Git，解密密钥只在服务器上。

---

## 十、轮换、备份与灾难恢复

### 10.1 轮换周期建议

| 对象 | 建议周期 |
|------|----------|
| TLS 证书 | 90 天（LE）自动续期 |
| mTLS 客户端证书 | 90~365 天 |
| SSH 用户证书 | 小时~天级 |
| API Token | 90 天 |
| GPG 主密钥 | 2~5 年（用子密钥日常） |

### 10.2 备份什么

- CA 私钥（**离线加密备份**，丢了就无法签发/验证）。
- Let's Encrypt 的 `/etc/letsencrypt`（含账户密钥与续期配置）。
- DNS API 凭据、`.env`、SOPS 解密密钥。

```bash
tar czf letsencrypt-backup.tar.gz /etc/letsencrypt
gpg --symmetric --cipher-algo AES256 letsencrypt-backup.tar.gz
```

### 10.3 灾难恢复演练

每季度做一次：在新机器上从备份恢复 `/etc/letsencrypt`，验证 `certbot renew --dry-run` 成功、站点正常。**没演练过的备份等于没有备份。**

---

## 十一、常见故障与排查

| 现象 | 原因 | 处理 |
|------|------|------|
| `certbot` 报 HTTP-01 失败 | 80 端口不通 / 反代拦截 | 放行 80 与 `/.well-known`，或改用 DNS-01 |
| 浏览器报 `NET::ERR_CERT_DATE_INVALID` | 证书过期 | 检查续期任务 |
| `SSL: CERTIFICATE_VERIFY_FAILED` | 缺中间证书 | Nginx 用 `fullchain.pem` |
| 证书链不完整 | 只配了 `cert.pem` | 换 `fullchain.pem` |
| 通配符签不下来 | 用了 HTTP-01 | 必须 DNS-01 |
| mTLS 报 400 | 服务端未信任客户端 CA | 检查 `ssl_client_certificate` |

排查神器：

```bash
openssl s_client -connect example.com:443 -servername example.com
# 看 "Verify return code" 与链
curl -vI https://example.com
```

---

## 十二、FAQ

**Q1：Let's Encrypt 有速率限制吗？**
A：有。同一域名每周 50 张、同一账户每 3 小时 300 张等。测试务必用 `--dry-run`，或先指向 staging 环境。

**Q2：私钥不小心提交到 GitHub 了怎么办？**
A：立即吊销并重签证书；轮换所有相关密钥与 Token；用 `git filter-repo` 清理历史（但历史可能已被镜像，视为已泄露）。

**Q3：一个证书能覆盖多少域名？**
A：LE 单证书最多 100 个 SAN 名称，且建议不超过 20 个，便于管理。多域名用通配符或分开签发。

**Q4：内网服务也需要公信证书吗？**
A：不一定。内网可用自建 CA + mTLS，比公信证书更贴合「零信任」；但对浏览器访问的内部站点，公信证书更省事。

**Q5：acme.sh 和 certbot 选哪个？**
A：有 Nginx 且习惯官方便用 certbot；需要大量 DNS 服务商支持、或想要无 Python 依赖的轻量方案用 acme.sh。

**Q6：如何验证证书真的在生效？**
A：`openssl s_client` 看链与到期日，`curl -vI` 看握手，外部可用 SSL Labs 评分。

**Q7：GPG 密钥丢了能恢复吗？**
A：不能。务必**离线备份主密钥**（写到纸上/加密 U 盘），日常用子密钥。

**Q8：怎么防止密钥在多台机器间乱传？**
A：用 SSH CA / Vault 动态凭据 / SOPS，把「分发密钥」变成「按需签发短期凭证」。

---

## 十三、相关资源

- [VPSVIP 官网](https://vpsvip.net) —— 稳定优化线路 VPS，适合承载证书签发与内网网关服务
- [ClashVIP](https://clashvip.net) —— 网络与节点资源
- [nav.clashvip.net](https://nav.clashvip.net) —— 导航与工具集合
- [clashhub.net](https://clashhub.net) —— 教程与文档
- [bbs.clashhub.net](https://bbs.clashhub.net) —— 社区讨论
- [clash-for-windows.net](https://clash-for-windows.net) —— 客户端下载
- [Let's Encrypt 文档](https://letsencrypt.org/docs/)
- [acme.sh](https://github.com/acmesh-official/acme.sh)
- [Caddy](https://caddyserver.com/)
- [SOPS](https://github.com/getsops/sops)
- [GnuPG](https://gnupg.org/)

---

## 免责声明

1. 本仓库内容仅供技术学习与参考；
2. 请遵守所在国家/地区法律法规以及各平台的使用条款；
3. 密钥与证书操作请在测试环境验证后再上生产，并保留回滚方案；
4. 私钥、CA 与备份请离线加密保存，切勿上传到公开位置。

## 许可证

MIT License

---
更新时间：2026-09-22
