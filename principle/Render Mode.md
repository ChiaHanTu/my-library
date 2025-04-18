# Client Side Render

1. 空 HTML 被送至瀏覽器
2. 瀏覽器下載並運行 JavaScript 
3. 畫面被渲染並具有互動性

> 頁面切換較為快速

![[CSR_principle.png]]


# Server Side Render

1. HTML 被送至瀏覽器並渲染到畫面上
2. 瀏覽器在背景下載並運行 JavaScript
3. 進行 Hydration 注入 JavaScript，賦予畫面互動性

> 有利於 SEO (Search Engine Optimization 搜尋引擎優化)

![[SSR_principle.png]]

--- 

# Static Site Generation 

1. 在 build 過程中，將 HTML、CSS 結合生成靜態頁面
2. 執行預渲染，根據特定的路由和數據生成多個靜態頁面實例
3. build 完成後，SSG 會將生成的靜態頁面輸出到特定資料夾中，這些頁面包含所有需要的 HTML、CSS、JavaScript，以及靜態資源
4. 由於不需要動態生成，可以被高效暫存，提供更好性能

---

## Nuxt Hybrid Rendering 

> 允許依照路由定義不同的快取模式


## SWR - Stale While Revalidate 

> 在可配置的 TTL (time to live) 下，添加快取 headers - *stale-while-revalidate* 存取來自 server 的 response，為 Node-server 的 Nitro 預設即會快取完整的 response，當 TTL 過期時，快取的 response 會回傳，同時頁面會在背景中重新產生，再次刷新後更新畫面。

## ISR - Incremental Static Regeneration

> 與 SWR 行為相同，但可將 response 存取在 CDN 快取上（目前 Netlify 與 Vercel 支援）。


## Nuxt Edge-Side Rendering

> 允許 Nuxt 應用渲染在鄰近使用者的 CDN 上，降低延遲性。當使用者請求頁面時，會尋找最近的 edge server，而非透過較遠的物理距離取得來自原 server 的 response，功能來自 Nitro。

---
## 註

- 渲染：
  指的是瀏覽器或 Server 將 JavaScript 編寫成的 Vue Components 解析為 HTML 元素。
   
- Hydration：
  指的是賦予靜態網頁互動性的過程