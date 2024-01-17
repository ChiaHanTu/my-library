
### for...in 迴圈

> 迭代對象的所有可枚舉屬性，包含自身屬性與從原型繼承的屬性

```JS
const obj = { a: 1, b: 2, c: 3 };

for (const key in obj) {
  console.log(key); // 'a', 'b', 'c'
  console.log(obj[key]); // 1, 2, 3
}
```


### for...of 迴圈

> 迭代對象的元素值，例如陣列、字串、Map、Set

```JS
const arr = [1, 2, 3];

for (const value of arr) {
  console.log(value); // 1, 2, 3
}
```
