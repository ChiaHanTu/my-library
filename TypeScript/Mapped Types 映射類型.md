
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
// 去除 readonly
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
// 去除 ?
type Concrete<Type> = {
	[Property in keyof Type]-?: Type[Property];
}

type MaybeUser = {
	id: string;
	name?: string;
	age?: string;
}

type User = Concrete<MaybeUser>;

type User = {
	id: string;
	name: string;
	age: string;
}
```


### Key remapping

```TS
type MappedTypeWithNewProperties<Type> = {
	[Properties in keyof Type as NewKeyType]: Type[Properties]
}

// 中間多一個反引號，處理 Lint 問題
type Getters<Type> = {
	[Property in keyof Type as `get${Capitalize<string & Property>}``]: () => Type[Property]
};


interface Person {
	name:  string;
	age: number;
	location: string;
}

type LazyPerson = Getters<Person>;

type LazyPerson = {
	getName: () => string;
	getAge: () => number;
	getLocation: () => string;
}
```

### Filter Type

```TS
type RemoveKindField<Type> = {
	[Property in keyof Type as Exclude<Property, "kind">]: Type[Property]
};

interface Circle {
	kind: "circle";
	radius: number;
}

type Kind
```
