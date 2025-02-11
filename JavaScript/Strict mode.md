
> 修正不合理行為，避免錯誤

## 禁止未聲明變數

```js
// 錯誤範例
"use strict";
x = 10;  // ReferenceError: x is not defined
```

## 禁止刪除不可刪除的屬性

```js
// 錯誤範例
"use strict";
delete Object.prototype;  // TypeError: Cannot delete property 'prototype' of function Object()
```

## 禁止函數內重複參數

```js
// 錯誤範例
"use strict";
function sum(a, a) {  // SyntaxError: Duplicate parameter name not allowed in this context
  return a + a;
}
```

## 禁止使用 with 雨具

```js
// 錯誤範例
"use strict";
with (Math) {  // SyntaxError: Strict mode code may not include a with statement
  console.log(PI);
}
```

## this 不能指向全局物件

```js
// 錯誤範例
"use strict";
function showThis() {
  console.log(this);  // undefined（在非嚴格模式下是 window）
}
showThis();
```

## 禁止使用 eval() 內部創建變數

```js
//錯誤範例
"use strict";
eval("var x = 10;");
console.log(x);  // ReferenceError: x is not defined
```


## 禁止 arguments.callee

```js
//錯誤範例
"use strict";
function factorial(n) {
  return n === 1 ? 1 : n * arguments.callee(n - 1);  // TypeError: 'caller', 'callee', and 'arguments' properties may not be accessed
}
```