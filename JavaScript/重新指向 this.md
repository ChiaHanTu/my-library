
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