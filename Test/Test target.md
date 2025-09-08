
# Display

- UI 與設計稿一致
- 各裝置尺寸正常顯示
- 中英文顯示正常

# Form

- 限定輸入字元
- 限制輸入長度
- 欄位驗證
- 新增 / 更新後更新列表資料
- Submit debounce
- 取消編輯後回復到原本狀態
- isDirty 時跳提醒
- 切換種類時，清除表單資料

# Function

- Try catch
- DRY principle
- Naming
- SOLID principle

# Props 

- 物件可以給預設值，讓使用物件中的 key 時，不會需要先判斷該 props 是否存在
```vue
props: {
	obj: {
		type: Object,
		default: () => {},
	}
}
```


