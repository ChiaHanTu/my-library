
## Header key

### Expires

> 存放在本地磁碟快取文件，讀取速度比 memory 慢，瀏覽器關閉時不會消失，適合大資源

```
Expires: Sat, 30 Nov 2024 12:15:00 GMT
```

如果瀏覽器收到這個 response ，就會把資源快取起來，下次使用者訪問時會檢視該使用者電腦本身的時間是否大於快取時間，如果超過的話就會重新發送請求，否則使用 cache

![[Pasted image 20241130122009.png]]

### Cache-control

> 存放在瀏覽器 memory 中，讀取速度比 disk 快，但瀏覽器關閉時會消失，適合小資源

可以設置 `max-age` 來決定 response 過期時間，如果和 `expires` 同時出現，會優先採用 `max-age` 

![[Pasted image 20241130122247.png]]
 
### Last-Modified & If-Modified-Since

```
last-modified: Wed, 14 Aug 2024 19:52:49 GMT
Cache-Control: max-age=31536000 // 一年
```

跟瀏覽器請求資源時，`last-modified` 可以記錄存取資源的時間，假設超過 `cache-control` 設定的時間，瀏覽器就會再跟 server 發送請求

```
GET /logo.png
If-Modified-Since: Wed, 14 Aug 2024 19:52:49 GMT
```

如果資源沒被更新過，瀏覽器就會返回 status code 304 (Not modified)，並繼續沿用先前的快取


### Etag & If-None-Match

Etag 可以比喻為快取檔案的 Hash 值，判斷檔案是否有更新，帶在 Response header 上，快取過期後瀏覽器可以拿此 Etag 確認檔案是否過期

```
GET /logo.png
If-None-Match: "bfc13a64729c4290ef5b2c2730249c88ca92d82d"
```

如果有新的回傳新的，沒有的話回傳 status code 304 (Not modified)


## 不使用快取的情境

### max-age=0

> 每一次造訪頁面都會送 request 去確認有無新檔案

首先收到 server response 

```
Cache-Control: max-age=0
Etag: "bfc13a64729c4290ef5b2c2730249c88ca92d82d"
```

再發出 request

```
If-None-Match: "bfc13a64729c4290ef5b2c2730249c88ca92d82d"
```

###  
---

參考來源：

[循序漸進理解 HTTP Cache 機制 · Issue #20 · aszx87410/blog (github.com)](https://github.com/aszx87410/blog/issues/20)