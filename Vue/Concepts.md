
### watchEffect

> 會監聽所有可訪問的響應性屬性

### ref

> 持有非原始值時，會通過 reactive 轉換為響應式代理


```js
const count = ref(0)
const state = reactive({
  count
})

console.log(state.count) // 0

state.count = 1
console.log(count.value) // 1
```

如果將一個新的 ref 賦值給一個關聯了已有 ref 的屬性，那麼它會替換掉舊的 ref：

```js
const otherCount = ref(2)

state.count = otherCount
console.log(state.count) // 2
// 原始 ref 現在已經和 state.count 失去聯繫
console.log(count.value) // 1
```

當 ref 作為響應式數組或原生集合類型 (如 `Map`) 中的元素被訪問時，它不會被解包：

```js
const books = reactive([ref('Vue 3 Guide')])
// 這裡需要 .value
console.log(books[0].value)

const map = reactive(new Map([['count', ref(0)]]))
// 這裡需要 .value
console.log(map.get('count').value)
```

### v-for

> 多層嵌套

```js
const sets = ref([
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10]
])

function even(numbers) {
  return numbers.filter((number) => number % 2 === 0)
}
```

```vue
<ul v-for="numbers in sets">
  <li v-for="n in even(numbers)">{{ n }}</li>
</ul>
```

### 