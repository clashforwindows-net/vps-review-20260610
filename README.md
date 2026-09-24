# VPS 闈欐€佺綉绔欐墭绠′笌 Jamstack 鐜颁唬鍓嶇鏋舵瀯瀹炴垬

**鍒嗙被**锛歏PS Web 鏋舵瀯 | **鏇存柊鏃ユ湡**锛?026-09-24 | **缁存姢浜?*锛歝lashforwindows-net

---

## 馃摉 鐩綍

- [涓€銆丣amstack 鏋舵瀯鏍稿績姒傚康](#涓€jamstack-鏋舵瀯鏍稿績姒傚康)
- [浜屻€侀潤鎬佺珯鐐圭敓鎴愬櫒瀵规瘮涓庨€夊瀷](#浜岄潤鎬佺珯鐐圭敓鎴愬櫒瀵规瘮涓庨€夊瀷)
- [涓夈€丯ginx 闈欐€佹枃浠舵湇鍔″櫒娣卞害閰嶇疆](#涓塶ginx-闈欐€佹枃浠舵湇鍔″櫒娣卞害閰嶇疆)
- [鍥涖€佽嚜寤洪潤鎬佺珯鐐规墭绠″钩鍙癩(#鍥涜嚜寤洪潤鎬佺珯鐐规墭绠″钩鍙?
- [浜斻€丠eadless CMS 闆嗘垚](#浜攈eadless-cms-闆嗘垚)
- [鍏€丆DN 杈圭紭缂撳瓨涓庡叏鐞冨垎鍙慮(#鍏璫dn-杈圭紭缂撳瓨涓庡叏鐞冨垎鍙?
- [涓冦€佽嚜鍔ㄦ瀯寤轰笌鎸佺画閮ㄧ讲锛圕I/CD锛塢(#涓冭嚜鍔ㄦ瀯寤轰笌鎸佺画閮ㄧ讲cicd)
- [鍏€佹€ц兘浼樺寲锛欳ore Web Vitals 瀹炴垬](#鍏€ц兘浼樺寲core-web-vitals-瀹炴垬)
- [涔濄€丠TTPS 涓庡畨鍏ㄩ厤缃甝(#涔漢ttps-涓庡畨鍏ㄩ厤缃?
- [鍗併€佺洃鎺с€佹棩蹇椾笌杩愮淮宸ュ叿閾綸(#鍗佺洃鎺ф棩蹇椾笌杩愮淮宸ュ叿閾?

---

## 涓€銆丣amstack 鏋舵瀯鏍稿績姒傚康

### 1.1 浠€涔堟槸 Jamstack

Jamstack 鏄竴绉嶇幇浠?Web 鏋舵瀯妯″紡锛屼唬琛?**J**avaScript銆?*A**PIs 鍜?**M**arkup銆傚畠閫氳繃鍦ㄦ瀯寤烘椂棰勬覆鏌撻潤鎬?HTML锛屽皢鍐呭閮ㄧ讲鍒?CDN 杈圭紭鑺傜偣锛屽疄鐜颁紶缁熷姩鎬?Web 鏋舵瀯鏃犳硶杈惧埌鐨勬€ц兘鍜屽畨鍏ㄦ按骞筹細

```
浼犵粺鏋舵瀯锛氬鎴风 鈫?搴旂敤鏈嶅姟鍣?鈫?鏁版嵁搴?鈫?妯℃澘寮曟搸 鈫?HTML 鈫?鍝嶅簲
                鈫?姣忔璇锋眰瀹炴椂娓叉煋

Jamstack锛氭瀯寤烘椂 鈫?棰勬覆鏌?HTML 鈫?CDN 杈圭紭 鈫?瀹㈡埛绔紙鐩存帴鏈嶅姟锛?                     鈫?涓€娆℃瀯寤猴紝鏃犳暟璁块棶
```

### 1.2 Jamstack 鐨勬牳蹇冧紭鍔?
| 浼樺娍缁村害 | 鍏蜂綋琛ㄧ幇 | 閲忓寲鏁版嵁 |
|---------|---------|---------|
| **鎬ц兘** | CDN 灏辫繎鍒嗗彂锛岄娓叉煋 HTML | 棣栧瓧鑺傛椂闂达紙TTFB锛? 50ms |
| **瀹夊叏** | 鏃犳湇鍔″櫒绔唬鐮侊紝鍑忓皯鏀诲嚮闈?| OWASP Top 10 椋庨櫓闄嶄綆 80% |
| **鎵╁睍鎬?* | CDN 鑷姩鍏ㄧ悆鍒嗗彂锛屾棤闇€鏋舵瀯璋冩暣 | 杞绘澗搴斿鐧句竾绾у苟鍙?|
| **鎴愭湰** | 闈欐€佹枃浠舵墭绠℃垚鏈瀬浣?| 姣斾紶缁?VPS 鎵樼鑺傜渷 60-90% |
| **寮€鍙戣€呬綋楠?* | 鐗堟湰鎺у埗銆丆I/CD銆侀瑙堥儴缃?| 閮ㄧ讲棰戠巼鎻愬崌 10x |

### 1.3 浣曟椂閫傚悎浣跨敤 Jamstack

**閫傚悎 Jamstack**锛?- 浼佷笟瀹樼綉銆佸崥瀹€佹枃妗ｇ珯锛堝唴瀹圭浉瀵归潤鎬侊級
- 鐢靛晢浜у搧灞曠ず椤碉紙鍟嗗搧淇℃伅鐢?CMS 绠＄悊锛?- 钀ラ攢钀藉湴椤碉紙楂樺苟鍙戞椿鍔ㄩ〉闈級
- 鍦ㄧ嚎鏂囨。锛圙itBook銆乂itePress銆丏ocusaurus锛?- 涓汉浣滃搧闆嗐€佺畝鍘嗙珯鐐?
**涓嶉€傚悎 Jamstack**锛?- 闇€瑕佸疄鏃舵暟鎹殑搴旂敤锛堣偂浠枫€佸疄鏃惰亰澶╋級
- 鐢ㄦ埛鐢熸垚鍐呭涓轰富鐨勫钩鍙帮紙璁哄潧銆佺ぞ浜ょ綉缁滐級
- 闇€瑕佸鏉傛暟鎹簱鏌ヨ鐨勫悗鍙扮郴缁?- 楂樺害浜や簰鐨?Web 搴旂敤锛堝彲鑰冭檻 Next.js SSR 娣峰悎鏂规锛?
---

## 浜屻€侀潤鎬佺珯鐐圭敓鎴愬櫒瀵规瘮涓庨€夊瀷

### 2.1 涓绘祦 SSG 鍏ㄩ潰妯瘎

| 宸ュ叿 | 璇█ | 妯℃澘寮曟搸 | 鏋勫缓閫熷害 | 涓婚鐢熸€?| SEO 鍙嬪ソ | 閫傚悎鍦烘櫙 | 鎺ㄨ崘鎸囨暟 |
|------|------|---------|---------|---------|---------|---------|---------|
| **Hugo** | Go | Go Template | 鈿?鏋侀€燂紙浜氱绾э級 | 涓板瘜 | 鉁?鍘熺敓 | 鍗氬/鏂囨。 | 猸愨瓙猸愨瓙猸?|
| **Hexo** | Node.js | EJS/Nunjucks | 蹇?| 鏋佷赴瀵?| 鉁?| 鍗氬 | 猸愨瓙猸愨瓙 |
| **Jekyll** | Ruby | Liquid | 鎱?| 涓板瘜 | 鉁?| 鍗氬/GitHub Pages | 猸愨瓙猸愨瓙 |
| **Gatsby** | React/Node.js | React | 鎱紙澶х珯锛?| 鏋佷赴瀵?| 鉁?| 澶嶆潅绔欑偣 | 猸愨瓙猸?|
| **Next.js** | React/Node.js | React | 涓瓑 | 涓板瘜 | 鉁?| 娣峰悎搴旂敤 | 猸愨瓙猸愨瓙猸?|
| **VitePress** | Vue/Node.js | Vue | 蹇?| 涓€鑸?| 鉁?| 鎶€鏈枃妗?| 猸愨瓙猸愨瓙 |
| **Docusaurus** | React/Node.js | MDX | 涓瓑 | 涓€鑸?| 鉁?| 寮€婧愭枃妗?| 猸愨瓙猸愨瓙 |
| **Astro** | 澶氭鏋?| Astro | 鈿?蹇?| 鏂板叴 | 鉁?| 鍐呭绔?| 猸愨瓙猸愨瓙猸?|
| **Eleventy** | Node.js | 澶氬紩鎿?| 蹇?| 杈冨皯 | 鉁?| 鍗氬/鏂囨。 | 猸愨瓙猸愨瓙 |
| **Zola** | Rust | Tera | 鈿?鏋侀€?| 鏂板叴 | 鉁?| 鍗氬/鏂囨。 | 猸愨瓙猸愨瓙 |

### 2.2 Hugo 娣卞害瀹炴垬锛堟帹鑽愭柟妗堬級

Hugo 鏄綋鍓嶆渶蹇殑闈欐€佺珯鐐圭敓鎴愬櫒锛屾绉掔骇鏋勫缓閫熷害锛岀壒鍒€傚悎鍐呭鏇存柊棰戠箒鐨勭珯鐐癸細

```bash
# Linux/macOS 瀹夎 Hugo
# macOS: brew install hugo
# Linux: snap install hugo

# 鎴栦娇鐢ㄨ剼鏈畨瑁咃紙鎺ㄨ崘锛?curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest \
    | grep browser_download_url \
    | grep extended_.*linux_amd64.tar.gz \
    | cut -d '"' -f 4 \
    | wget -qi -
tar -xf hugo_*_linux-amd64.tar.gz
mv hugo /usr/local/bin/
rm hugo_*_linux-amd64.tar.gz
hugo version
```

### 2.3 Hugo 绔欑偣鍒濆鍖栦笌涓婚閰嶇疆

```bash
# 鍒涘缓鏂扮珯鐐?hugo new site my-site --format yaml
cd my-site

# 鍒濆鍖?Git
git init

# 瀹夎涓婚锛圥aperMod - 楂樻€ц兘 SEO 鍙嬪ソ涓婚锛?git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod

# 缂栬緫閰嶇疆鏂囦欢
cat > hugo.yaml << 'EOF'
baseURL: "https://example.com/"
languageCode: "zh-cn"
title: "鎴戠殑鎶€鏈崥瀹?
theme: "PaperMod"
enableRobotsTXT: true
enableEmoji: true

# 瀵艰埅鑿滃崟
menu:
  main:
    - name: 鍗氬
      url: /posts/
      weight: 1
    - name: 鍏充簬
      url: /about/
      weight: 2

# 鍒嗛〉
pagination:
  pagerSize: 10

# SEO
params:
  description: "鎶€鏈崥瀹紝鍒嗕韩 VPS銆丏evOps銆佺綉缁滀紭鍖栫粡楠?
  keywords: ["VPS", "DevOps", "Linux", "缃戠粶"]
  author: "clashforwindows-net"
  images: ["og-image.jpg"]
  showBreadcrumbs: true
  showTOC: true
  tocOpen: false

# 鎬ц兘浼樺寲
minify:
  disableXML: true
  minifyOutput: true

build:
  writeStats: true  # 鐢熸垚璧勬簮鏄犲皠锛岀敤浜?CDN 缂撳瓨鎺у埗

imaging:
  quality: 85
  formats: ["webp", "jpeg"]
EOF
```

### 2.4 鍐呭鍒涗綔涓?Markdown 楂樼骇鐢ㄦ硶

```markdown
---
title: "VPS 缃戠粶浼樺寲瀹屽叏鎸囧崡"
date: 2026-09-24
draft: false
tags: ["VPS", "Linux", "缃戠粶浼樺寲", "BBR"]
categories: ["杩愮淮瀹炶返"]
description: "娣卞害瑙ｆ瀽 VPS 缃戠粶浼樺寲鏂规锛屼粠 BBR 鍒伴攼閫燂紝浠庡唴鏍歌皟浼樺埌鍗忚浼樺寲"
cover:
  image: "images/cover.jpg"
  alt: "VPS 缃戠粶浼樺寲"
  relative: true
slug: vps-network-optimization-guide

# 楂樼骇鍔熻兘
outputs: ["html", "json"]  # 鏀寔澶氭牸寮忚緭鍑猴紙JSON 鐢ㄤ簬 API锛?type: post

# 璇勮绯荤粺
comments: true
---

# 姝ｆ枃寮€濮?
Hugo 鏀寔 Shortcodes锛堢煭浠ｇ爜锛夛紝鍙墿灞?Markdown 鍔熻兘锛?
{{< figure src="/images/diagram.png" title="鏋舵瀯鍥? >}}

{{< callout type="info" >}}杩欐槸涓€涓彁绀烘{{< /callout >}}

鏇村鍐呭...
```

### 2.5 Next.js 闈欐€佸鍑猴紙娣峰悎鏂规锛?
```javascript
// next.config.js - 閰嶇疆闈欐€佸鍑?/** @type {import('next').NextConfig} */
const nextConfig = {
  output: 'export',           // 鍚敤闈欐€佸鍑?  images: {
    unoptimized: true         // 闈欐€佸鍑洪渶瑕佸叧闂浘鐗囦紭鍖?  },
  trailingSlash: true,         // 鐢熸垚 foo/index.html 鑰岄潪 foo.html
  basePath: '',               // 鐢熶骇鐜璺緞鍓嶇紑
  assetPrefix: './',           // 闈欐€佽祫婧愮浉瀵硅矾寰?}

module.exports = nextConfig
```

```javascript
// app/posts/[slug]/page.js
// 浣跨敤 App Router 瀹炵幇闈欐€佽矾寰?export async function generateStaticParams() {
  const posts = await getAllPosts()
  return posts.map(post => ({ slug: post.slug }))
}

export default async function PostPage({ params }) {
  const post = await getPostBySlug(params.slug)
  return (
    <article>
      <h1>{post.title}</h1>
      <div dangerouslySetInnerHTML={{ __html: post.content }} />
    </article>
  )
}
```

```bash
# 鏋勫缓骞跺鍑?npm run build
# 鐢熸垚 out/ 鐩綍锛屽寘鍚墍鏈夐潤鎬佹枃浠?# 鍙洿鎺ラ儴缃插埌 Nginx 鎴?CDN
```

---

## 涓夈€丯ginx 闈欐€佹枃浠舵湇鍔″櫒娣卞害閰嶇疆

### 3.1 鐢熶骇绾?Nginx 閰嶇疆

```nginx
# /etc/nginx/sites-available/static-site.conf

# 涓婃父閰嶇疆锛堝彲閫夎礋杞藉潎琛★級
upstream static_origin {
    server 127.0.0.1:8080;
    keepalive 32;
}

# 涓绘湇鍔″櫒鍧?server {
    listen 80;
    listen [::]:80;
    server_name example.com www.example.com;

    # HTTP 鑷姩璺宠浆 HTTPS
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name example.com www.example.com;

    # SSL 閰嶇疆锛圠et's Encrypt锛?    ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
    ssl_trusted_certificate /etc/letsencrypt/live/example.com/chain.pem;

    # SSL 瀹夊叏閰嶇疆
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384;
    ssl_prefer_server_ciphers off;
    ssl_session_cache shared:SSL:10m;
    ssl_session_timeout 1d;
    ssl_stapling on;
    ssl_stapling_verify on;

    # 瀹夊叏鍝嶅簲澶?    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header X-XSS-Protection "1; mode=block" always;
    add_header Referrer-Policy "strict-origin-when-cross-origin" always;
    add_header Permissions-Policy "camera=(), microphone=(), geolocation=()" always;
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;

    # Gzip 鍘嬬缉
    gzip on;
    gzip_vary on;
    gzip_proxied any;
    gzip_comp_level 6;
    gzip_types text/plain text/css text/xml application/json application/javascript
               application/xml application/xml+rss text/javascript application/x-javascript
               image/svg+xml font/opentype;

    # Brotli 鍘嬬缉锛堟洿楂樺帇缂╃巼锛?    # 闇€瑕?nginx 缂栬瘧浜?brotli 妯″潡
    # brotli on;
    # brotli_types text/plain text/css text/xml application/json application/javascript
    #            application/xml application/xml+rss text/javascript;

    # 闈欐€佹枃浠舵牴鐩綍
    root /var/www/static-site;
    index index.html;

    # 瀛楃闆?    charset utf-8;

    # 璁块棶鏃ュ織锛圝SON 鏍煎紡渚夸簬鍒嗘瀽锛?    log_format main_json escape=json
        '{ "@timestamp": "$time_iso8601", '
        '"remote_addr": "$remote_addr", '
        '"request": "$request", '
        '"status": $status, '
        '"bytes_sent": $body_bytes_sent, '
        '"request_time": $request_time, '
        '"http_referer": "$http_referer", '
        '"http_user_agent": "$http_user_agent", '
        '"gzip_ratio": "$gzip_ratio" }';

    access_log /var/log/nginx/access.log main_json;
    error_log /var/log/nginx/error.log warn;

    # 闈欐€佽祫婧愮紦瀛樼瓥鐣ワ紙闀挎湡缂撳瓨锛?    location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|woff|woff2|ttf|eot|webp|avif)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
        # 楠岃瘉鏂囦欢鍙樺寲锛圗Tag锛?        etag on;
        # 绂佹鏃ュ織璁板綍闈欐€佽祫婧愶紙鍑忓皯 I/O锛?        access_log off;
    }

    # HTML 鏂囦欢锛氱煭鏈熺紦瀛樺苟寮哄埗閲嶆柊楠岃瘉
    location ~* \.html$ {
        expires -1;
        add_header Cache-Control "no-cache, no-store, must-revalidate";
        etag on;
    }

    # 鏍硅矾寰勫拰 SPA 璺敱
    location / {
        try_files $uri $uri/ /index.html;
    }

    # 闈欐€佺洰褰曪紙鏄惧紡璺緞锛?    location /images/ {
        alias /var/www/static-site/images/;
        autoindex off;
        # 鍥剧墖澶勭悊锛堥渶瑕?nginx-http-image 妯″潡鎴?lua锛?        # image_filter resize 800 600;
    }

    # 鏂囨。鐩綍
    location /docs/ {
        alias /var/www/static-site/docs/;
        autoindex on;  # 鐩綍娴忚锛堝叧闂垯 off锛?        default_type text/plain;
    }

    # 绂佹璁块棶鏁忔劅鏂囦欢
    location ~ /\.(?!well-known) {
        deny all;
        return 404;
    }

    location ~* \.(htaccess|htpasswd|git|svn|env|DS_Store)$ {
        deny all;
        return 404;
    }

    # 鎬ц兘锛氬紑鍚?TCP 浼樺寲
    tcp_nopush on;
    tcp_nodelay on;
    sendfile on;

    # 杩炴帴鏁伴檺鍒?    limit_conn addr 100;
    limit_req zone=req_limit burst=50 nodelay;

    # 闃茬埇铏?    if ($http_user_agent ~* (crawl|spider|bot|scraper)) {
        return 403;
    }
}
```

### 3.2 閫熺巼闄愬埗閰嶇疆

```nginx
# /etc/nginx/conf.d/rate-limit.conf

# 璇锋眰閫熺巼闄愬埗锛堥槻 CC 鏀诲嚮锛?limit_req_zone $binary_remote_addr zone=req_limit:10m rate=10r/s;

# 杩炴帴鏁伴檺鍒讹紙闃茬埇铏級
limit_conn_zone $binary_remote_addr zone=addr:10m;

# 鎸夋湇鍔″櫒鏁翠綋闄愬埗
limit_zone conn_limit_per_server $server_name 10m;
```

### 3.3 Brotli 鍘嬬缉鏀寔锛圢ginx 缂栬瘧妯″潡锛?
```bash
# 妫€鏌ユ槸鍚﹀凡缂栬瘧 brotli 妯″潡
nginx -V 2>&1 | grep brotli

# 濡傛灉娌℃湁锛屼娇鐢ㄥ姩鎬佹ā鍧楁柟寮忓畨瑁?# 1. 涓嬭浇 ngx_brotli 婧愮爜
git clone --depth 1 https://github.com/google/ngx_brotli.git
cd ngx_brotli
git submodule update --init

# 2. 鑾峰彇褰撳墠 nginx 缂栬瘧鍙傛暟
nginx -V 2>&1 | grep -oP "configure arguments:.*"

# 3. 閲嶆柊缂栬瘧 nginx锛堣拷鍔?brotli 妯″潡锛?# 鍙傝€冧笂鏂归厤缃弬鏁帮紝杩藉姞 --add-module=../ngx_brotli
```

---

## 鍥涖€佽嚜寤洪潤鎬佺珯鐐规墭绠″钩鍙?
### 4.1 Caddy 鑷姩 HTTPS 閮ㄧ讲鏂规

Caddy 鏄幇浠?Web 鏈嶅姟鍣紝鍐呯疆鑷姩 HTTPS锛岄€傚悎涓嶆兂鎶樿吘 Nginx 閰嶇疆鐨勭敤鎴凤細

```bash
# 瀹夎 Caddy
sudo apt-get install -y debian-keyring debian-archive-keyring apt-transport-https
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' \
    | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' \
    | sudo tee /etc/apt/sources.list.d/caddy-stable.list
sudo apt-get update && sudo apt-get install caddy

# Caddyfile 閰嶇疆锛堢畝娲佽娉曪級
cat > /etc/caddy/Caddyfile << 'EOF'
example.com {
    root * /var/www/static-site
    encode gzip zstd

    # 鑷姩 TLS锛堣嚜鍔ㄤ粠 Let's Encrypt 鐢宠璇佷功锛?    tls admin@example.com

    # 鏂囦欢鏈嶅姟
    file_server

    # SPA 璺敱鏀寔
    try_files {path} {path}/ /index.html

    # 缂撳瓨鎺у埗
    @static {
        file *.css *.js *.png *.jpg *.jpeg *.gif *.ico *.svg *.woff *.woff2
    }
    header @static Cache-Control "public, max-age=31536000, immutable"

    # 瀹夊叏澶?    header {
        X-Frame-Options "SAMEORIGIN"
        X-Content-Type-Options "nosniff"
        Referrer-Policy "strict-origin-when-cross-origin"
        Permissions-Policy "camera=(), microphone=(), geolocation=()"
        Strict-Transport-Security "max-age=31536000; includeSubDomains"
    }

    # 鏃ュ織
    log {
        output file /var/log/caddy/access.log
        format json
    }
}
EOF

systemctl enable --now caddy
```

### 4.2 鑷缓绫?Netlify 閮ㄧ讲骞冲彴锛圢etlify Drop 寮€婧愭浛浠ｏ級

浣跨敤寮€婧愬伐鍏锋瀯寤哄畬鏁寸殑闈欐€佺珯鐐规墭绠″钩鍙帮細

```yaml
# docker-compose.yml - 鑷缓闈欐€佹墭绠″钩鍙?version: '3.8'
services:
  # 鏂囦欢涓婁紶鏈嶅姟锛圢etlify Drop 鏇夸唬锛?  drop:
    image: surjithctly/netlify-drop:latest
    ports:
      - "3000:3000"
    environment:
      - SITE_TITLE=My Static Hosting
      - MAX_FILE_SIZE=52428800  # 50MB
    volumes:
      - ./sites:/app/sites
      - ./uploads:/app/uploads
    restart: unless-stopped

  # 鐩翠紶鏂囦欢鏈嶅姟
  caddy:
    image: caddy:2-alpine
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./Caddyfile:/etc/caddy/Caddyfile
      - ./www:/var/www/html
    restart: unless-stopped

  # Git-based CI/CD锛圵oodpecker CI锛?  woodpecker:
    image: woodpeckerci/woodpecker-server:latest
    ports:
      - "8000:8000"
    environment:
      - WOODPECKER_OPEN=true
      - WOODPECKER_ADMIN=admin
      - WOODPECKER_GITHUR=true
    volumes:
      - ./woodpecker-data:/var/lib/woodpecker
    restart: unless-stopped
```

---

## 浜斻€丠eadless CMS 闆嗘垚

### 5.1 Strapi 鑷墭绠★紙鏈€娴佽鐨勫紑婧?Headless CMS锛?
```yaml
# docker-compose.yml - Strapi + PostgreSQL
version: '3.8'
services:
  strapi:
    image: strapi/strapi:4.25
    environment:
      DATABASE_CLIENT: postgres
      DATABASE_HOST: strapi-db
      DATABASE_PORT: 5432
      DATABASE_NAME: strapi_cms
      DATABASE_USERNAME: strapi
      DATABASE_PASSWORD: ${DB_PASSWORD}
      JWT_SECRET: ${JWT_SECRET}
      ADMIN_JWT_SECRET: ${ADMIN_JWT_SECRET}
      APP_KEYS: ${APP_KEYS}
      API_TOKEN_SALT: ${API_TOKEN_SALT}
    volumes:
      - ./strapi-app:/app
      - ./uploads:/app/public/uploads
    depends_on:
      - strapi-db
    restart: unless-stopped

  strapi-db:
    image: postgres:15-alpine
    environment:
      POSTGRES_DB: strapi_cms
      POSTGRES_USER: strapi
      POSTGRES_PASSWORD: ${DB_PASSWORD}
    volumes:
      - ./postgres-data:/var/lib/postgresql/data
    restart: unless-stopped
```

### 5.2 Hugo 涓?Strapi 闆嗘垚鑴氭湰

```bash
#!/bin/bash
# sync-strapi.sh - 浠?Strapi CMS 鑾峰彇鍐呭骞跺悓姝ュ埌 Hugo
set -e

STRAPI_URL="${STRAPI_URL:-http://localhost:1337}"
STRAPI_TOKEN="${STRAPI_TOKEN}"
CONTENT_DIR="content/posts"

echo "=== 鍚屾 Strapi 鍐呭鍒?Hugo ==="

mkdir -p "$CONTENT_DIR"

# 鑾峰彇鎵€鏈夋枃绔?ARTICLES=$(curl -s -H "Authorization: Bearer $STRAPI_TOKEN" \
    "${STRAPI_URL}/api/articles?populate=*&pagination[pageSize]=100" \
    | jq -r '.data[] | @json')

if [ -z "$ARTICLES" ]; then
    echo "[WARN] 鏈幏鍙栧埌鏂囩珷锛岃妫€鏌?API Token 鍜?URL"
    exit 1
fi

echo "$ARTICLES" | while IFS= read -r article; do
    slug=$(echo "$article" | jq -r '.attributes.slug')
    title=$(echo "$article" | jq -r '.attributes.title')
    content=$(echo "$article" | jq -r '.attributes.content')
    date=$(echo "$article" | jq -r '.attributes.publishedAt' | sed 's/T.*//')
    tags=$(echo "$article" | jq -r '[.attributes.tags.data[].attributes.name] | join(", ")')

    # 鐢熸垚 Hugo Markdown 鏂囦欢
    cat > "${CONTENT_DIR}/${slug}.md" << FRONT
---
title: "${title}"
date: ${date}
draft: false
tags: [${tags}]
categories: ["CMS鏂囩珷"]
description: "$(echo "$article" | jq -r '.attributes.summary // "鏂囩珷鎽樿"')"
slug: ${slug}
cms_id: $(echo "$article" | jq -r '.id')
---

${content}
FRONT

    echo "[OK] 宸插悓姝? ${slug}"
done

echo ""
echo "=== 鏋勫缓绔欑偣 ==="
hugo --gc --minify
echo "鏋勫缓瀹屾垚锛岃緭鍑虹洰褰? public/"
```

### 5.3 Astro + Strapi 闈欐€佺敓鎴?
```javascript
// astro.config.mjs
import { defineConfig } from 'astro/config';
import react from '@astrojs/react';
import node from '@astrojs/node';

export default defineConfig({
    integrations: [react()],
    output: 'static',
    build: {
        assets: '_assets'
    },
    vite: {
        build: {
            cssCodeSplit: true,
            rollupOptions: {
                output: {
                    // 闀挎湡缂撳瓨鍝堝笇
                    entryFileNames: '_assets/[name].[hash].js',
                    chunkFileNames: '_assets/[name].[hash].js',
                    assetFileNames: '_assets/[name].[hash][extname]'
                }
            }
        }
    }
});
```

```javascript
// src/pages/index.astro - 浠?Strapi 鑾峰彇鏁版嵁
---
import Layout from '../layouts/Layout.astro';
import Card from '../components/Card.astro';

// 鏋勫缓鏃朵粠 Strapi 鑾峰彇鏁版嵁
const response = await fetch(
    `${import.meta.env.STRAPI_URL}/api/articles?populate=*&sort=publishedAt:desc&pagination[limit]=20`
);
const { data } = await response.json();

const articles = data.map(item => ({
    id: item.id,
    title: item.attributes.title,
    slug: item.attributes.slug,
    summary: item.attributes.summary,
    publishedAt: item.attributes.publishedAt,
    cover: item.attributes.cover?.data?.attributes?.url
}));
---

<Layout title="鎴戠殑鍗氬">
    <main>
        <div class="grid">
            {articles.map(article => (
                <Card
                    title={article.title}
                    href={`/posts/${article.slug}`}
                    body={article.summary}
                    cover={article.cover ? `${import.meta.env.STRAPI_URL}${article.cover}` : null}
                />
            ))}
        </div>
    </main>
</Layout>
```

---

## 鍏€丆DN 杈圭紭缂撳瓨涓庡叏鐞冨垎鍙?
### 6.1 鑷缓 CDN 鍒嗗彂绛栫暐

```
鍏ㄧ悆鐢ㄦ埛璇锋眰
       鈹?       鈻?鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹?鈹? DNS 鏅鸿兘瑙ｆ瀽  鈹?鈫? 鏍规嵁鐢ㄦ埛 IP 杩斿洖鏈€杩戣妭鐐?鈹斺攢鈹€鈹€鈹€鈹€鈹€鈹攢鈹€鈹€鈹€鈹€鈹€鈹?       鈹?  鈹屸攢鈹€鈹€鈹€鈹粹攢鈹€鈹€鈹€鈹攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹?  鈻?        鈻?         鈻?         鈻?鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹?鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹?鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹?鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹?鈹?HK鑺傜偣 鈹?鈹?TK鑺傜偣 鈹?鈹?LA鑺傜偣 鈹?鈹?DE鑺傜偣 鈹?鈹?VPS   鈹?鈹?VPS   鈹?鈹?VPS   鈹?鈹?VPS   鈹?鈹?婧愮珯) 鈹?鈹?缂撳瓨) 鈹?鈹?缂撳瓨) 鈹?鈹?缂撳瓨) 鈹?鈹斺攢鈹€鈹€鈹€鈹€鈹€鈹?鈹斺攢鈹€鈹€鈹€鈹€鈹€鈹?鈹斺攢鈹€鈹€鈹€鈹€鈹€鈹?鈹斺攢鈹€鈹€鈹€鈹€鈹€鈹?```

### 6.2 Nginx 婧愮珯閰嶇疆锛堜緵 CDN 鍥炴簮锛?
```nginx
server {
    listen 8080;
    server_name origin.example.com;

    root /var/www/static-site;
    index index.html;

    # 鍏佽 CDN 鍥炴簮鐨?IP 娈碉紙Cloudflare銆侀樋閲屼簯绛夛級
    allow 10.0.0.0/8;
    allow 172.16.0.0/12;
    allow 192.168.0.0/16;
    deny all;

    location / {
        try_files $uri $uri/ =404;
        add_header X-Cache-Status "ORIGIN";
    }
}
```

### 6.3 Cloudflare Workers 杈圭紭閲嶅畾鍚?
```javascript
// cloudflare-worker-cdn-redirect.js
// 浣跨敤 Cloudflare Workers 瀹炵幇澶?CDN 婧愮珯鍋ュ悍妫€鏌ヤ笌鑷姩鍒囨崲
// 鍙湪鑷缓杈圭紭鑺傜偣涓婅繍琛岋紙浣跨敤 workerd 鍏煎杩愯鏃讹級

export default {
    async fetch(request, env, ctx) {
        const url = new URL(request.url);

        // 鍋ュ悍妫€鏌ョ鐐?        if (url.pathname === '/health') {
            const start = Date.now();
            try {
                const origin = await checkOriginHealth('https://origin.example.com');
                return new Response(JSON.stringify({
                    status: 'ok',
                    origin_healthy: origin,
                    response_time: Date.now() - start
                }), { headers: { 'Content-Type': 'application/json' } });
            } catch (e) {
                return new Response(JSON.stringify({ status: 'error', message: e.message }), {
                    status: 503,
                    headers: { 'Content-Type': 'application/json' }
                });
            }
        }

        // 涓昏矾鐢憋細鎸夊湴鐞嗕綅缃€夋嫨鏈€浼樻簮绔?        const country = request.headers.get('cf-ipcountry') || 'US';
        const colo = request.cf?.colo || 'UNKNOWN';

        const originMap = {
            'HK': 'https://hk.example.com',
            'TW': 'https://hk.example.com',
            'SG': 'https://hk.example.com',
            'JP': 'https://jp.example.com',
            'KR': 'https://jp.example.com',
            'US': 'https://us.example.com',
            'DE': 'https://de.example.com',
            'GB': 'https://de.example.com',
            'default': 'https://hk.example.com'
        };

        const origin = originMap[country] || originMap['default'];

        // 缂撳瓨閿紙涓嶅惈鍥藉/colo 鍙傛暟锛?        const cacheKey = new Request(url.toString(), { headers: {} });
        const cache = caches.default;
        let response = await cache.match(cacheKey);

        if (!response) {
            response = await fetch(origin + url.pathname + url.search, {
                cf: { cacheKey, cacheEverything: true, cacheTtl: 86400 }
            });
            ctx.waitUntil(cache.put(cacheKey, response.clone()));
        }

        // 娣诲姞鍏冧俊鎭ご
        const newHeaders = new Headers(response.headers);
        newHeaders.set('X-CDN-Node', colo);
        newHeaders.set('X-Origin-Country', country);

        return new Response(response.body, {
            status: response.status,
            headers: newHeaders
        });
    }
};

async function checkOriginHealth(origin) {
    const controller = new AbortController();
    const timeout = setTimeout(() => controller.abort(), 3000);
    try {
        const res = await fetch(origin + '/health', { signal: controller.signal });
        clearTimeout(timeout);
        return res.ok;
    } catch {
        clearTimeout(timeout);
        return false;
    }
}
```

---

## 涓冦€佽嚜鍔ㄦ瀯寤轰笌鎸佺画閮ㄧ讲锛圕I/CD锛?
### 7.1 Woodpecker CI 鑷姩鍖栨瀯寤洪厤缃?
```yaml
# .woodpecker.yml
workspace:
    base: /build
    path: site

steps:
    1-clone:
        image: alpine/git:latest
        commands:
            - git clone --depth 1 https://github.com/clashforwindows-net/my-site.git .
            - git submodule update --init --recursive

    2-build:
        image: peaceiris/actions-hugo:v0.125.0
        commands:
            - hugo --gc --minify --environment production
            - echo "Build completed at $(date)"
        settings:
            resources:
                memory: 512m

    3-test:
        image: node:20-alpine
        commands:
            - npx html-validate dist/index.html || true
            - npx lighthouse https://example.com --output=json --output-path=./lh-report.json --chrome-flags="--headless" || true
        when:
            - event: [pull_request, tag]

    4-deploy:
        image: appleboy/drone-scp:latest
        settings:
            host:
                from_secret: VPS_HOST
            user: root
            key:
                from_secret: VPS_SSH_KEY
            target: /var/www/static-site
            source: ./public/*
            command: |
                systemctl reload nginx || true
        when:
            - event: [push, tag]

    5-notify:
        image: alpine
        commands:
            - apk add --no-cache curl jq
            - 'curl -X POST https://api.telegram.org/bot$TELEGRAM_BOT_TOKEN/sendMessage -d "chat_id=$TELEGRAM_CHAT_ID" -d "text=Site deployed! Status: $$DRONE_BUILD_STATUS"'
        when:
            - status: [success, failure]
```

### 7.2 GitHub Actions 鑷姩鍖栭儴缃?
```yaml
# .github/workflows/deploy.yml
name: Build and Deploy

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
        - uses: actions/checkout@v4
          with:
              submodules: recursive
              fetch-depth: 1

        - name: Setup Hugo
          uses: peaceiris/actions-hugo@v3
          with:
              hugo-version: '0.130.0'
              extended: true

        - name: Build
          run: hugo --gc --minify

        - name: Setup Pages
          uses: actions/configure-pages@v4

        - name: Upload artifact
          uses: actions/upload-pages-artifact@v3
          with:
              path: ./public

        - name: Deploy to GitHub Pages
          id: deployment
          uses: actions/deploy-pages@v4
          if: github.ref == 'refs/heads/main'
```

---

## 鍏€佹€ц兘浼樺寲锛欳ore Web Vitals 瀹炴垬

### 8.1 Core Web Vitals 鍩哄噯涓庣洰鏍?
| 鎸囨爣 | 鍚箟 | 杈炬爣鏍囧噯 | 浼樺寲鎵嬫 |
|------|------|---------|---------|
| **LCP** | 鏈€澶у唴瀹圭粯鍒?| < 2.5s 鉁?| 棰勫姞杞藉叧閿祫婧愩€丆DN 缂撳瓨銆佸帇缂╁浘鐗?|
| **FID/INP** | 棣栨杈撳叆寤惰繜 | < 100ms 鉁?| 浠ｇ爜鍒嗗壊銆佸欢杩熷姞杞?JS銆佸噺灏戜富绾跨▼闃诲 |
| **CLS** | 绱Н甯冨眬鍋忕Щ | < 0.1 鉁?| 鍥哄畾鍥剧墖/瑙嗛灏哄銆侀鍔犺浇瀛椾綋銆侀伩鍏嶅姩鎬佹敞鍏?|

### 8.2 Lighthouse CI 鑷姩鍖栨祴璇?
```javascript
// lighthouserc.js - Lighthouse CI 閰嶇疆
module.exports = {
    ci: {
        collect: {
            url: [
                'http://localhost/',           // 棣栭〉
                'http://localhost/posts/',       // 鏂囩珷鍒楄〃
                'http://localhost/about/'       // 鍏充簬椤甸潰
            ],
            numberOfRuns: 3,
            startServerCommand: 'hugo server --bind 0.0.0.0',
            startServerReadyPattern: 'Web Server is available'
        },
        assert: {
            assertions: {
                'categories:performance': ['error', { minScore: 0.9 }],
                'categories:accessibility': ['error', { minScore: 0.9 }],
                'first-contentful-paint': ['warn', { maxNumericValue: 2000 }],
                'largest-contentful-paint': ['error', { maxNumericValue: 2500 }],
                'cumulative-layout-shift': ['error', { maxNumericValue: 0.1 }],
                'interactive': ['error', { maxNumericValue: 3000 }],
                'uses-optimized-images': 'warn',
                'uses-webp-images': 'warn',
                'uses-long-cache-ttl': 'warn'
            }
        },
        upload: {
            target: 'lhci',
            serverBaseUrl: 'http://localhost:9001'
        }
    }
};
```

### 8.3 鍥剧墖浼樺寲鑷姩鍖栬剼鏈?
```bash
#!/bin/bash
# optimize-images.sh - 鑷姩鍘嬬缉鍏ㄧ珯鍥剧墖骞惰浆鎹负 WebP/AVIF
# 闇€瑕? apt-get install webp libavif-tools imagemagick oxipng

set -e
SOURCE_DIR="${1:-./static/images}"
QUALITY="${2:-80}"

echo "=== 鍥剧墖浼樺寲寮€濮?==="
echo "婧愮洰褰? $SOURCE_DIR"
echo "璐ㄩ噺: $QUALITY%"

find "$SOURCE_DIR" -type f \( -iname "*.jpg" -o -iname "*.jpeg" -o -iname "*.png" \) | while read -r img; do
    filename="${img%.*}"
    ext="${img##*.}"

    # 1. PNG 浼樺寲锛坥xipng锛?    if [ "${ext,,}" = "png" ]; then
        oxipng -o 6 --strip safe "$img" -o "$img" 2>/dev/null || true
    fi

    # 2. 鐢熸垚 WebP锛坈webp锛?    if command -v cwebp &> /dev/null; then
        cwebp -q "$QUALITY" "$img" -o "${filename}.webp" 2>/dev/null || true
        # 濡傛灉鍘熷鏂囦欢鏄?JPEG锛屼繚鐣欏師鍥句綔涓?AVIF 澶囬€?    fi

    # 3. 鐢熸垚 AVIF锛坅vifenc锛?    if command -v avifenc &> /dev/null; then
        avifenc -q "$QUALITY" -s 8 "$img" "${filename}.avif" 2>/dev/null || true
    fi

    # 4. 閿愬寲锛堝鐓х墖绫诲浘鐗囷級
    if [ "${ext,,}" = "jpg" ] || [ "${ext,,}" = "jpeg" ]; then
        mogrify -unsharp 0.5x0.5+0.5+0 -quality "$QUALITY" "$img" 2>/dev/null || true
    fi

    echo "[OK] $img"
done

echo ""
echo "=== 浼樺寲瀹屾垚 ==="
echo "鎬绘枃浠舵暟: $(find "$SOURCE_DIR" -type f \( -iname "*.jpg" -o -iname "*.jpeg" -o -iname "*.png" \) | wc -l)"
```

---

## 涔濄€丠TTPS 涓庡畨鍏ㄩ厤缃?
### 9.1 Let's Encrypt 鑷姩缁湡

```bash
#!/bin/bash
# cert-renew.sh - 鑷姩缁湡璇佷功骞堕噸杞?Nginx
# 浣跨敤 certbot 鐨?DNS-01 楠岃瘉锛堟敮鎸侀€氶厤绗﹁瘉涔︼級

CERT_DIR="/etc/letsencrypt/live/example.com"
DOMAIN="example.com"
WILDCARD_DOMAIN="*.example.com"

# DNS API 瀵嗛挜锛圕loudflare 涓轰緥锛?CF_API_KEY="your-cloudflare-api-key"
CF_EMAIL="admin@example.com"

echo "=== 璇佷功缁湡妫€鏌?==="

if [ -d "$CERT_DIR" ]; then
    EXPIRY_DATE=$(openssl x509 -in "$CERT_DIR/fullchain.pem" -noout -enddate 2>/dev/null | cut -d= -f2)
    EXPIRY_EPOCH=$(date -d "$EXPIRY_DATE" +%s 2>/dev/null || echo "0")
    NOW_EPOCH=$(date +%s)
    DAYS_LEFT=$(( ($EXPIRY_EPOCH - $NOW_EPOCH) / 86400 ))

    echo "璇佷功鍒版湡: $EXPIRY_DATE"
    echo "鍓╀綑澶╂暟: $DAYS_LEFT"

    if [ "$DAYS_LEFT" -lt 30 ]; then
        echo "璇佷功鍗冲皢鍒版湡锛?$DAYS_LEFT澶╋級锛屽紑濮嬬画鏈?.."
        certbot certonly \
            --dns-cloudflare \
            --dns-cloudflare-credentials /root/.cloudflare.ini \
            -d "$DOMAIN" \
            -d "$WILDCARD_DOMAIN" \
            --email "$CF_EMAIL" \
            --agree-tos \
            --non-interactive \
            --keep-until-expiring

        # 閲嶈浇鏈嶅姟
        systemctl reload nginx
        systemctl reload caddy || true
        echo "[OK] 璇佷功宸茬画鏈燂紝鏈嶅姟宸查噸杞?
    else
        echo "璇佷功灏氭湁 $DAYS_LEFT 澶╂湁鏁堟湡锛屾棤闇€缁湡"
    fi
else
    echo "[ERROR] 璇佷功鐩綍涓嶅瓨鍦? $CERT_DIR"
fi
```

### 9.2 HSTS 棰勫姞杞戒笌瀹夊叏閰嶇疆

```nginx
# 瀹夊叏澶村畬鏁撮厤缃紙鏀惧叆 server 鍧楋級
add_header Strict-Transport-Security
    "max-age=31536000; includeSubDomains; preload"
    always;
# preload 涓虹敵璇?HSTS 棰勫姞杞藉垪琛紝浣跨敤鍓嶇‘淇濆煙鍚嶅畬鍏ㄦ敮鎸?HTTPS
```

---

## 鍗併€佺洃鎺с€佹棩蹇椾笌杩愮淮宸ュ叿閾?
### 10.1 闈欐€佺珯鐐瑰仴搴风洃鎺ц剼鏈?
```bash
#!/bin/bash
# health-monitor.sh - 闈欐€佺珯鐐瑰彲鐢ㄦ€х洃鎺?# 閰嶅悎 cron 浣跨敤锛?/5 * * * * /opt/monitoring/health-monitor.sh

SITE_URL="${1:-http://localhost}"
ALERT_THRESHOLD=3
LOG_FILE="/var/log/site-health.log"

check_site() {
    local url=$1
    local start_time=$(date +%s%3N)

    # 鑾峰彇 HTTP 鐘舵€佺爜鍜屽搷搴旀椂闂?    HTTP_CODE=$(curl -sL -o /dev/null -w "%{http_code}" --max-time 10 "$url")
    RESPONSE_TIME=$(($(date +%s%3N) - start_time))

    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    local status="OK"

    if [ "$HTTP_CODE" -ne 200 ]; then
        status="FAIL"
    elif [ "$RESPONSE_TIME" -gt 2000 ]; then
        status="SLOW"
    fi

    echo "{\"timestamp\":\"$timestamp\",\"url\":\"$url\",\"status\":\"$status\",\"http_code\":$HTTP_CODE,\"response_time_ms\":$RESPONSE_TIME}" >> "$LOG_FILE"

    if [ "$status" != "OK" ]; then
        echo "[ALERT] $url - $status (HTTP $HTTP_CODE, ${RESPONSE_TIME}ms)"
        # 鍙戦€佸憡璀︼紙鍙€?Telegram/閽夐拤锛?        curl -s -X POST "https://api.telegram.org/bot$TELEGRAM_BOT/sendMessage" \
            -d "chat_id=$TELEGRAM_CHAT" \
            -d "text=鈿狅笍 闈欐€佺珯鐐瑰憡璀? $url - $status" > /dev/null
    fi
}

# 鐩戞帶涓荤珯鍜屽叧閿〉闈?check_site "${SITE_URL}/"
check_site "${SITE_URL}/sitemap.xml"
check_site "${SITE_URL}/robots.txt"
```

### 10.2 绔欑偣鍒嗘瀽浠〃鏉匡紙Python 杞婚噺鏂规锛?
```python
#!/usr/bin/env python3
"""
static-site-analytics.py - 杞婚噺绾ч潤鎬佺珯鐐瑰垎鏋?"""
import json
import re
from collections import Counter
from datetime import datetime
from pathlib import Path

def analyze_access_log(log_file: str) -> dict:
    """鍒嗘瀽 Nginx JSON 鏍煎紡鏃ュ織锛岃緭鍑虹珯鐐硅闂粺璁?""
    page_views = 0
    unique_ips = Counter()
    status_codes = Counter()
    pages = Counter()
    response_times = []
    errors = []

    with open(log_file) as f:
        for line in f:
            try:
                entry = json.loads(line)
                page_views += 1
                unique_ips[entry['remote_addr']] += 1
                status_codes[entry['status']] += 1
                pages[entry['request'].split()[1]] += 1
                if entry.get('request_time'):
                    response_times.append(float(entry['request_time']))
                if entry['status'] >= 400:
                    errors.append(entry)
            except (json.JSONDecodeError, KeyError):
                continue

    # 璁＄畻缁熻鏁版嵁
    avg_response = sum(response_times) / len(response_times) if response_times else 0
    p95_response = sorted(response_times)[int(len(response_times) * 0.95)] if response_times else 0

    return {
        'page_views': page_views,
        'unique_visitors': len(unique_ips),
        'top_pages': pages.most_common(10),
        'status_breakdown': dict(status_codes),
        'error_count': sum(1 for e in errors),
        'avg_response_ms': round(avg_response * 1000, 2),
        'p95_response_ms': round(p95_response * 1000, 2)
    }

if __name__ == '__main__':
    stats = analyze_access_log('/var/log/nginx/access.log')
    print(f"=== 绔欑偣璁块棶缁熻 ===")
    print(f"椤甸潰娴忚閲? {stats['page_views']:,}")
    print(f"鐙珛璁垮: {stats['unique_visitors']}")
    print(f"骞冲潎鍝嶅簲: {stats['avg_response_ms']}ms")
    print(f"P95 鍝嶅簲: {stats['p95_response_ms']}ms")
    print(f"閿欒璇锋眰: {stats['error_count']}")
    print("\nTop 10 椤甸潰:")
    for path, count in stats['top_pages']:
        print(f"  {count:5d}  {path}")
```

---

## 馃敆 鎺ㄥ箍鍏ュ彛

**銆怌lashVIP 鏈哄満鎺ㄨ崘銆?*锛歔https://nav.clashvip.net](https://nav.clashvip.net) | [https://clashvip.net](https://clashvip.net)  
**銆怴PS 浼樻儬鎺ㄨ崘銆?*锛歔https://vpsvip.net](https://vpsvip.net)  
**銆怌lash for Windows 瀹㈡埛绔€?*锛歔https://clash-for-windows.net](https://clash-for-windows.net)  
**銆怌lashHub 绀惧尯銆?*锛歔https://bbs.clashhub.net](https://bbs.clashhub.net) | [https://clashhub.net](https://clashhub.net)

---

> 馃搮 鏈€鍚庢洿鏂帮細2026-09-24 | 瑙夊緱鏈夌敤锛熻缁欎粨搴撲竴涓?猸? 
> 鈿欙笍 鏈粨搴撻€傞厤 VPS 闈欐€佺珯鐐规墭绠°€丣amstack 鏋舵瀯涓庣幇浠ｅ墠绔儴缃插満鏅€?