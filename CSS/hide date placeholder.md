
 [參考](https://stackoverflow.com/questions/28686288/remove-default-text-placeholder-present-in-html5-input-element-of-type-date)

```CSS

&--hide-placeholder {
	&::-webkit-datetime-edit-text,
	&::-webkit-datetime-edit-year-field,
	&::-webkit-datetime-edit-month-field,
	&::-webkit-datetime-edit-day-field,
	&::-webkit-datetime-edit-hour-field,
	&::-webkit-datetime-edit-minute-field,
	&::-webkit-datetime-edit-ampm-field,
	&::-webkit-calendar-picker-indicator {
		@apply hidden;
	}
}
```