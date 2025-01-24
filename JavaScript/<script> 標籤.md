
## < script >

- 同步執行

> 頁面加載時，遇到 `<script>` 會立即停止解析 HTML，開始加載及執行 JavaScript，頁面渲染會被阻塞，直到 sciprt 加載和執行完成

## < script async >

- 異步加載

> 背景執行，不會阻塞 HTML 解析，加載完成後立即執行，可能會在 HTML 完全解析之前執行

## < script defer >

- 異步加載

> 背景執行，不會阻塞 HTML 解析，但腳本的執行會延遲到 HTML 解析完成時執行

