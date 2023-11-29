在看了 google 搜尋頁的 CSP 後發現他們沒有特別加上 style-src 的設置，所以去研究了 CSS injection 可能會從哪些地方攻擊，看了文章後目前發現可能會引發攻擊的原因有二，第一是利用 CSS 選擇器（圖二），當選擇器選到符合某條件元素時發送 request 取得某 url 的資源，這時接收 request 的攻擊者 server 就會知道 input 的 value 屬性裡面的字元，進而多次載入 style 以逐步取得使用者輸入的完整資料（CSRF token），而這種攻擊方式會發生在即時同步內容的網站，因著其即時載入新的 style 的特性。第二種方式則是在非即時載入 style 的頁面利用 @import  的方式（圖三），逐步載入上一種方式的 CSS （圖二）以取得使用者資料。 參考：[https://blog.huli.tw/2022/09/29/css-injection-1/](https://blog.huli.tw/2022/09/29/css-injection-1/)而避免第一種攻擊可以藉由 img-src 的限制，防止載入其他網頁的資源，以避免 `background: url(...)`  
這種攻擊，避免第二種攻擊則是藉由 style-src 的 url 限制，阻擋其他來源的 CSS import 。因此可以考慮採用這些方式來阻擋 CSS injection 的攻擊，因為不開 `unsafe-inline` 但卻需要容許使用套件 CSS、和容許本地 inline-style 會需要花費非常多的時間成本執行



![[Pasted image 20231123100724.png]]

![[Pasted image 20231123100733.png]]

![[Pasted image 20231123100744.png]]

