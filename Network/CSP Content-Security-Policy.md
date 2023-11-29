> 用以偵測與減輕特定形式的攻擊，包含 XSS、data injection...

[參考連結](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy)

---
# Fetch directive 

用以控制存取資源的來源位址，包含下列幾種


### default-src  [參考連結](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/default-src)

> 做為每種 fetch directive 的備選值，例如：假使 script-src 無明確定義，就會採用 default-src 的設定

### child-src

> 定義 Web workers 與 `<frame>` 和 `<iframe>` 的授權來源

### connect-src

> 限制連結來源，例如 `<a>`, `fetch()`, `XMLHttpRequest`, `WebSocket`, `EventSource`, `Navigator.sendBeacon()`

### font-src

> 針對 `@font-face` 限制文字存取來源

### frame-src

> 定義 `<frame>` 和 `<iframe>` 的授權來源

### img-src

> 定義圖片與圖示（favicons） 的授權來源

### manifest

> 定義清單檔案（manifest files） 的授權來源

### media-src

> 定義 `<audio>` , `<vidio>`, `<track>` 的授權來源

### object-src

> 定義 `<object>` , `<embed>`的授權來源

### prefetch-src

> 定義 prefetched 或 prerendered 的授權來源

### script-src

> 定義 JavaScript 和 WebAssembly 的授權來源

### script-src-elem

> 定義 `<script>` 的授權來源

### style-src

>定義 stylesheets 的授權來源

### style-src-elem

> 定義 `<style>` 與 `<link rel="stylesheet">` 的授權來源

### style-src-attr

> 設定可存取的 inline-style 樣式。若設定為 `style-src-attr: 'none'`，以下狀況皆不會應用到 DOM 元素上

``` HTML
<div style="display:none">Foo</div>
```

``` JS
document.querySelector("div").setAttribute("style", "display:none;");
document.querySelector("div").style.cssText = "display:none;";
```

以下狀況不會被攔截，除非有設定相對應的 `script-src` source

```JS
document.querySelector("div").style.display = "none";
```


### worker-src

> 定義 Worker, SharedWorker, ServiceWorker 的 Scripts 授權來源

--- 

# Document directives

管理文件或 Worker 環境中的策略應用的屬性


### base-uri

> 限制可以使用在文件 `<base>` 中的 URLs 

### sandbox

> 允許 sandbox 可以請求的資源對象，類似於 `<iframe>` 中的 sandbox attribute.

---

# Navigation directives 

管理使用者可以導向或是提交表單的 locations 

###  form-action

> 限制表單提交的對象位址

### form-ancestors

> 定義允許可能會使用 `<frame>`, `<iframe>`, `<object>`, `<embed>` 嵌入 page 的元素的 parents

### navigate-to (experimental)

> 限制在 `<form>` （如果 form-action 沒有定義的話）, `<a>`, `window.location`, `window.open` 中可以導轉過去的URLs 


---

# Reporting directives 

控制違反 CSP 的回報過程 - 參照 [`Content-Security-Policy-Report-Only`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy-Report-Only)


## report-to

> 指名使用者代理儲存錯誤回報的目的地

``` JSON
Report-To: { 
	"group": "endpoint-1",
	"max_age": 10886400,
	"endpoints": [
		{ "url": "https://example.com/reports" },
		{ "url": "https://backup.com/reports" }
	]
}

Content-Security-Policy: …; report-to endpoint-1
```


---

# Other directives 

### require-trusted-types-for (experimental)

> Enforces Trusted Types at the DOM XSS injection sinks.

### trusted-types (experimental)

> Used to specify an allowlist of [Trusted Types](https://w3c.github.io/trusted-types/dist/spec/) policies. Trusted Types allows applications to lock down DOM XSS injection sinks to only accept non-spoofable, typed values in place of strings.

### upgrade-insecure-requests

> Instructs user agents to treat all of a site's insecure URLs (those served over HTTP) as though they have been replaced with secure URLs (those served over HTTPS). This directive is intended for websites with large numbers of insecure legacy URLs that need to be rewritten.


--- 

# 值


## Keyword Values


### none

>  不允許存取任何資源

### self

> 允許當前 domain 的資源

### strict-dynamic

> 允許在已經通過 nonce or hash 信任的 domain 執行動態 script，尤其是在應用程式中使用諸如動態腳本生成的框架時。它允許這些框架在不需要逐一列舉所有資源的情況下運行，而僅通過動態載入的方式來構建執行腳本的內容。

### report-sample

> 要求在違規報告中包含違規程式碼範例



## Unsafe keyword values


### unsafe-inline

> 允許行內資源

### unsafe-eval

> 允許動態程式碼像是 `eval`, `setTimeout`, `window.execScript`

### unsafe-hashes

> 允許特定 hash 值（ex: `'sha256-abcdef1234567890'`）的內嵌 script 



## Hosts values


### Host

> 允許來自指定 host 的資源，例如：
  `example.com`, `*.example.com`, `https://*.example.com:12/path/to/file.js`
  
> 允許來自符合特定路徑的資源，例如：
  `example.com/api/` 會配對像是 `example.com/api/users/new` 的 URLs

> 限縮路徑的資源存取，例如：
  `example.com/file.js` 會配對 `http://example.com/file.js` 和 `https://example.com/file.js`, 非 `https://example.com/file.js/file2.js`.
  
### Scheme

> 允許存取特定 scheme 的資源，例如：`https:`, `http:`, `data:`



## Other values


### nonce-* 

> 允許特定加密後配對的 script 元素，每次 server 都要在傳遞的過程中產出一個獨一無二的 nonce 值，例如：

  ```JS
<script nonce="DhcnhD3khTMePgXwdayK9BsMqXjhguVV">
```

### sha*- 

> script-src `sha256-jzgBGA4UWFFmpOBq0JpdsySukE1FrEN5bUpoK8Z29fY=`.

---
### 註

1. `Manifest files`:  
   web 應用的元資訊，讓使用者能將網站添加到主畫面或啟動應用程式，範例：

```json
	{
	  "name": "My Web App", 
	  "short_name": "WebApp",
	  "description": "A description of my web app.",
	  "start_url": "/",
	  "display": "standalone",
	  "background_color": "#ffffff",
	  "theme_color": "#000000",
	  "icons": [ 
	    {
	      "src": "/icon.png",
	      "sizes": "192x192",
	      "type": "image/png"
	     }
	   ]
     }
```

2. `WebAssembly`: 
   低級的、面向網頁的執行代碼格式，為二進制指令格式，可以高效地在瀏覽器中執行，並可以與 JavaScript 一起工作。
   
   -  可以運行在 x86、RAM 等
   -  適合高性能計算的應用，例如遊戲、模擬器、圖型繪製等
   -  可與 JavaScript 相互操作與調用
   -  運行在沙盒環境中，設有安全機制如範圍檢查和內存安全檢查，防止常見的安全漏洞

3. 若設定多個 CSP 政策，那麼只會採取最後一個設定的 CSP

---   
   
### 參考資料：

-  **x86:**
    
    - x86 是一種常見的處理器架構，最初由英特爾（Intel）和 AMD（Advanced Micro Devices）開發。
    - x86 架構最初是設計用於個人電腦（PC）和伺服器，因此它在桌面和伺服器領域中非常流行。
    - 常見的 x86 處理器包括 Intel 的 Core 和 Xeon 系列，以及 AMD 的 Ryzen 和 EPYC 系列。

- **ARM:**
    
    - ARM（Advanced RISC Machine）是一種精簡指令集計算機（RISC）架構，最初由ARM Holdings（現為NVIDIA旗下）開發。
    - ARM 架構主要設計用於嵌入式系統、行動設備和低功耗應用。它在智能手機、平板電腦和物聯網設備中得到廣泛應用。
    - ARM 架構的特點是精簡且節能，適合移動設備和其他對電池壽命和效能有較高要求的應用。
    - 許多智能手機和平板電腦使用 ARM 架構的處理器，例如蘋果的  A 系列（例如A14 Bionic）和高通的 Snapdragon 系列。

   
