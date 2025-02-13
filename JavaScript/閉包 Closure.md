> 閉包（Closure）是函式以及該函式被宣告時所在的作用域環境（lexical environment）的組合。

- 內部函式能夠取得函式外部的變數，並且記住這個變數。

###  狀態保存

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

### 緩存機制

```js
function cached(fn) {
  const cache = {};

  // 被回傳的箭頭函式，可以取得外面的 cache 變數，同時記住這個變數
  // 因此可以把這個 cache 拿來存已經計算的結果
  return (...args) => {
    // 把輸入字符串化並當成 key
    const key = JSON.stringify(args);

    // 如果 key 已經在 cache 中，則不用重複算，直接回傳之前存的運算結果
    // 如果 key 還不在，則運算完後，把 key 與運算結果放到 cache 中，未來可以避免重複運算
    if (key in cache) {
      return cache[key];
    } else {
      const val = fn(...args);
      cache[key] = val;
      return val;
    }
  };
}
```

### 模擬私有變數

```js
// privateCounter 沒被法被外部修改，
// 因為閉包的關係 increment 與 decrement 可以存取到 privateCounter
// 因此 privateCounter 只能夠透過 increment 與 decrement 來改，這能有效避免被誤觸到
var counter = (function () {
  var privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function () {
      changeBy(1);
    },
    decrement: function () {
      changeBy(-1);
    },
    value: function () {
      return privateCounter;
    },
  };
})();

console.log(counter.value()); // logs 0
counter.increment();
counter.increment();
console.log(counter.value()); // logs 2
counter.decrement();
console.log(counter.value()); // logs 1
```