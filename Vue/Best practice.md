
## Props 穩定性

在 Vue 之中，一個子組件只會在其至少一個 props 改變時才會更新

```vue
<ListItem
  v-for="item in list"
  :id="item.id"
  :active-id="activeId" />
```

上例會在每次 `activeId` 改變時觸發列表每個元素的更新，理想下只有活躍的組件才需要更新

```vue
<ListItem
  v-for="item in list"
  :id="item.id"
  :active="item.id === activeId" />
```

因此可以改用狀態比對來取代，只會在 `active` 狀態更改時才會更新

## 計算屬性的穩定性

```js
const computedObj = computed(() => {
  return {
    isEven: count.value % 2 === 0
  }
})
```

如果計算屬性回傳一個物件，則每次都會判定新舊值始終不同

```js
const computedObj = computed((oldValue) => {
  const newValue = {
    isEven: count.value % 2 === 0
  }
  if (oldValue && oldValue.isEven === newValue.isEven) {
    return oldValue
  }
  return newValue
})
```

可以手動比較新舊值來優化

## 減少大型不可變數據的響應性開銷

使用 `shallowRef()` 或是 `shallowReactive()` 繞開深度響應，但代價是，我們現在必須將所有深層級對象視為不可變的，並且只能通過替換整個根狀態來觸發更新：

```js
const shallowArray = shallowRef([
  /* 巨大的列表，裡面包含深層的對象 */
])

// 這不會觸發更新...
shallowArray.value.push(newObject)
// 這才會觸發更新
shallowArray.value = [...shallowArray.value, newObject]

// 這不會觸發更新...
shallowArray.value[0].foo = 1
// 這才會觸發更新
shallowArray.value = [
  {
    ...shallowArray.value[0],
    foo: 1
  },
  ...shallowArray.value.slice(1)
]
```

## 組件實例的數量

> 以大型列表渲染為例，若為了抽象化邏輯而創建太多的組件實例將會導致性能損失，因此在此狀況下需特別留意



