
### watchEffect

> 會監聽所有可訪問的響應性屬性

### ref

> 持有非原始值時，會通過 reactive 轉換為響應式代理


```js
const books = reactive([ref('Vue 3 Guide')])
// 這裡需要 .value
console.log(books[0].value)

const map = reactive(new Map([['count', ref(0)]]))
// 這裡需要 .value
console.log(map.get('count').value)

// 當 ref 作為響應式數組或原生集合類型 (如 `Map`) 中的元素被訪問時，它不會被解包：
```



