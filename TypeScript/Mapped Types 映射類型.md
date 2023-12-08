
### 索引簽名

> 用於聲明尚未提前聲明的屬性類型

```TS
type OnlyBoolsAndHorses = {
	[key: string]: boolean | Horse;
}

const conforms: OnlyBoolsAndHorses = {
	del: true,
	rodney: false
}
```

## 映射類型

> 使用 s Union 遍歷物件裡面的 key，創造 PropertyKey

```TS
type OptionsFlags<Type> = {
	[Property in keyof Type]: boolean;
}
```

### 映射修飾符 

> - modifier

```TS
type CreateMutable<Type> = {
	-readonly [Property in keyof Type]: Type[Property]
};

type LockedAccount = {
	readonly id: string;
	readonly name: string;
};

type UnlockedAccount = CreateMutable<LockedAccount>;

type UnlockedAccount = {
	id: string;
	name: string;
}
```

```TS
type Concrete<Type> = {
	[Property in keyof Type]: Type[Property];
}

type MaybeUser = {
	id: string;
	name?: string;
	age?: string;
}

type User = Concrete<MaybeUser>;

type User = 
```
