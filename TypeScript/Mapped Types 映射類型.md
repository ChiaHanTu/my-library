
### 索引簽名

> 用於聲明尚未提前聲明的屬性類型

```TS
type OnlyBoolsAndHorses = {
	[key: string]: boolean | Horse;
}
```