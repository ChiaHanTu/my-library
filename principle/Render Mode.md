# Client Side Render

1. HTML 被送至瀏覽器並渲染到畫面上
2. 瀏覽器在背景下載並運行 JavaScript 
3. 進行 Hydration 注入 JavaScript，賦予畫面互動性

![[SSR_principle.png]]

# Server Side Render

1. 空 HTML 被送至瀏覽器
2. 瀏覽器下載並運行 JavaScript 
3. 畫面被渲染並具有互動性

> 有利於 SEO (Search Engine Optimization 搜尋引擎優化)

![[CSR_principle.png]]

--- 
## Nuxt Hybrid Rendering 

> 允許依照路由定義不同的快取模式


## Stale White Revalidate

> 在可配置的 TTL (time to live) 下，添加快取 headers 存取來自 server 的 response，為 Node-server 的 Nitro 預設快取完整的 response，當 ＴＴ

---
## 註

- 渲染：
  指的是瀏覽器或 Server 將 JavaScript 編寫成的 Vue Components 解析為 HTML 元素。
   
- Hydration：
  指的是賦予靜態網頁互動性的過程