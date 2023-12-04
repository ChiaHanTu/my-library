
> 函數參數傳遞方式

## 傳值 Call by Value

> 當函數參數是 Call by Value 時，傳遞的是變數的值，函數內部對參數的修改不會影響原始變數

```JS
String, Boolean, Number...
```


## 傳址 Call by Reference 

> 遞的是變數的引用，函數內部對參數的修改會影響原始變數。

```JS
Object and Array
```


### ex: 

```JS
let num = 1;
let obj = { value: 1 };

function modify(a, b) {
	a = 2;
	b.value = 2;
}
 
modify(num, obj);
  
console.log(num); // 輸出：1
console.log(obj); // 輸出：{ value: 2 }
```

