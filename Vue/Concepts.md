
## lifecycle

![[Pasted image 20250210111127.png]]

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

### 事件處理

> Vue 預設在冒泡階段執行事件處理

```vue
<!-- 僅當 event.target 是元素本身時才會觸發事件處理器 -->
<!-- 例如：事件處理器不來自子元素 -->
<div @click.self="doThat">...</div>

<!-- 添加事件監聽器時，使用 `capture` 捕獲模式 -->
<!-- 例如：指向內部元素的事件，在被內部元素處理前，先被外部處理 -->
<div @click.capture="doThis">...</div>

<!-- 點擊事件最多被觸發一次 --> 
<a @click.once="doThis"></a>

<!-- 滾動事件的默認行為 (scrolling) 將立即發生而非等待 `onScroll` 完成 -->
<!-- 以防其中包含 `event.preventDefault()` -->
<!-- 通常用於 mobile -->
<div @scroll.passive="onScroll">...</div>
```

### v-model

> true-value and false-value

```vue
<input
  type="checkbox"
  v-model="toggle"
  true-value="yes"
  false-value="no" />
```

```vue
<!-- 在 "change" 事件後同步更新而不是 "input" -->
<input v-model.lazy="msg" />
```

### watchEffect

> 會監聽所有可訪問的響應性屬性，程式碼較簡潔，但依賴關係不明確


### emits

```typescript
// 事件校驗

const emit = defineEmits({
	// 無校驗
	click: null,
	// 校驗 submit 事件
	submit: ({ email, password }) => {
		if (email && password) {
			return true
		} else {
			console.warn('Invalid submit event payload!')
			return false
		}
	}
})

function submitForm(email, password) {
	emit('submit', { email, password })
}
```


### defineModel

> 返回值可以取得雙向綁定的值和修飾符

```typescript
// vue 3.4 後
// 設立自定義的修飾符
const [model, modifiers] = defineModel({
	set(value) {
		if (modifiers.capitalize) {
			return value.charAt(0).toUpperCase() + value.slice(1)
		}
		return value
	} 
})
```


```typescript
// vue 3.4 之前
const props = defineProps({
	modelValue: String,
	modelModifiers: { default: () => ({}) }
})

const emit = defineEmits(['update:modelValue'])

function emitValue(e) { 
	let value = e.target.value
	if (props.modelModifiers.capitalize) {
		value = value.charAt(0).toUpperCase() + value.slice(1)
	} 
	emit('update:modelValue', value)
}
```


### defineAsyncComponent

```typescript
const AsyncComp = defineAsyncComponent({
  // 加載函數
  loader: () => import('./Foo.vue'),

  // 加載異步組件時使用的組件
  loadingComponent: LoadingComponent,
  // 展示加載組件前的延遲時間，默認為 200ms
  delay: 200,

  // 加載失敗後展示的組件
  errorComponent: ErrorComponent,
  // 如果提供了一個 timeout 時間限制，並超時了
  // 也會顯示這裡配置的報錯組件，默認值是：Infinity
  timeout: 3000
})
```


### directive

```js
const app = createApp({})

// 使 v-focus 在所有組件中都可用
app.directive('focus', {
  /* ... */
})
```

```js
export default {
  setup() {
    /*...*/
  },
  directives: {
    // 在模板中啟用 v-focus
    focus: {
      /* ... */
    }
  }
}
```

```vue
<div v-example:foo.bar="baz">
```

example 指令帶了 foo 參數與 bar 修飾符，值為 baz

#### 指令鉤子

```js
const myDirective = {
  // 在綁定元素的 attribute 前
  // 或事件監聽器應用前調用
  created(el, binding, vnode, prevVnode) {
    // 下面會介紹各個參數的細節
  },
  // 在元素被插入到 DOM 前調用
  beforeMount(el, binding, vnode, prevVnode) {},
  // 在綁定元素的父組件
  // 及他自己的所有子節點都掛載完成後調用
  mounted(el, binding, vnode, prevVnode) {},
  // 綁定元素的父組件更新前調用
  beforeUpdate(el, binding, vnode, prevVnode) {},
  // 在綁定元素的父組件
  // 及他自己的所有子節點都更新後調用
  updated(el, binding, vnode, prevVnode) {},
  // 綁定元素的父組件卸載前調用
  beforeUnmount(el, binding, vnode, prevVnode) {},
  // 綁定元素的父組件卸載後調用
  unmounted(el, binding, vnode, prevVnode) {}
}
```

參考: https://zh-hk.vuejs.org/guide/reusability/custom-directives.html

