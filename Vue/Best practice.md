
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

可ㄧ