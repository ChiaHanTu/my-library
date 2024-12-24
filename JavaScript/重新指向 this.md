
###  Function.prototype.call

```js
function.call(thisArg, arg1, arg2, ...)


function greet(greeting, punctuation) {
    console.log(`${greeting}, ${this.name}${punctuation}`);
}

const person = { name: "Alice" };

greet.call(person, "Hello", "!");
// Output: "Hello, Alice!"
```


###  Function.prototype.apply

```js
function.apply(thisArg, [argsArray])

function greet(greeting, punctuation) {
    console.log(`${greeting}, ${this.name}${punctuation}`);
}

const person = { name: "Alice" };

greet.apply(person, ["Hello", "!"]);
// Output: "Hello, Alice!"
```


###  Function.prototype.bind()

```js
function.bind(thisArg, arg1, arg2, ...)

const person = {
    name: "Alice",
    greet: function(greeting) {
        console.log(`${greeting}, ${this.name}`);
    }
};

const greetBound = person.greet.bind({ name: "Bob" });
greetBound("Hello");
// Output: "Hello, Bob"
```

可以柯里化參數

```js
function add(a, b) {
    return a + b;
}

const addFive = add.bind(null, 5); // 預先固定 a = 5
console.log(addFive(10)); // Output: 15

// 其中第一個參數 a 被固定為 5。
```
