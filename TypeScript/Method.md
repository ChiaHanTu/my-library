
## infer

> 推導型別，只能在條件型別的 extends 語句中使用，並只能用來推導出在這個語句中出現的型別


### Tuple 

> 代表一個已知元素數量和類型的陣列

```TS
let x: [string, number];
x = ['hello, 10']
```

## Reverse

```TS
type Reverse<S extends string> =

S extends `${infer F}${infer R}` ? `${Reverse<R>}${F}` : S;


// test
type test_0_actual = Reverse<'rehsaD'>;
type test_0_expected = 'Dasher';
```

## Exclude

```TS
type Exclude<T, U> = T extends U ? never : T;
```


### SuffixTester 

```TS
type SuffixTester<T extends string, U extends string> = T extends `${string} ${U}` ? true : false;
```

### Protector

```TS
type Protector<T = object> = {
	+readonly [P in keyof T]: T[P] extends Function 
	? T[P]
	: T[P] extends object
	? Protector<T[P]>
	: T[P];
};
```


## Counter

```TS
type Fill<T extends number, Acc extends Array<number> = []> = T extends Acc['length'] ? Acc[number] : Fill<T, [...Acc, Acc['length']]>;
  
type Counter<Start extends number, End extends number> = Exclude<Fill<End>, Fill<Start>> | End;
```