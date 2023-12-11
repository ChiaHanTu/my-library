
## infer

> 推導型別，只能在條件型別的 extends 語句中使用，並只能用來推導出在這個語句中出現的型別


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
type SuffixTester<T extends string, U extends string> =

T extends `${infer F} ${infer R}` ? U extends F ? true : U extends R ? true : SuffixTester<R, U> : false;
```