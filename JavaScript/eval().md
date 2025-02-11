> 內建函數，可以執行傳入的字串作為 JS 程式碼

```js
console.log(eval("2 + 2")); // 4
```

```js
let x = 10;
eval("x = 20;");
console.log(x); // 20
```

```js
eval("function sayHello() { return 'Hello!'; }");
console.log(sayHello()); // "Hello!"
```

1. 容易導致 XSS 攻擊
2. 性能問題，需要 JS 解析器重新解析和執行程式碼
3. 在 strict mode 下不會影響外部作用域

```js
// 錯誤範例
"use strict";
eval("var x = 10;");
console.log(x); // ReferenceError: x is not defined
```