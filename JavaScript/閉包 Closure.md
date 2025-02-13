> 閉包（Closure）是函式以及該函式被宣告時所在的作用域環境（lexical environment）的組合。

- 內部函式能夠取得函式外部的變數，並且記住這個變數。

```js
// 因為閉包的關係，getState 與 setState 可以取得與記得 state
function useState(initialState) {
  let state = initialState;

  function getState() {
    return state;
  }

  function setState(updatedState) {
    state = updatedState;
  }
  return [getState, setState];
}

const [count, setCount] = useState(0);

count(); // 0
setCount(1);
count(); // 1
setCount(500);
count(); // 500
```

