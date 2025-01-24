
> CSS 渲染區塊，以 float 的方式與其他區塊互動，此區塊與外部環境之間的佈局互不干擾

符合以下其中一個條件即滿足：

1. 根元素
2. `float` 有設值（非 none）
3. `position: absolute or position: fixed`
4. `display: inline-block`
5. `display: table` 或是隱式創建為 table cells 的元素
6. `overflow` 不為 `visible` or `clip`
7. `display: flow-root`（將元素創建為一個 BFC）
8. `<button>`, `<input type="button"> display: flow-root`
9. `contain: layout, contain: paint, contain: content`
10. 