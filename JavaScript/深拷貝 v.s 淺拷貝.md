
## 淺拷貝 Shallow Copy

> 當進行淺拷貝時，如果對象的屬性值是基本數據類型，則直接複製值；如果屬性值是對象或對象數組，則複製對象的引用，而不是實際的對象。這意味著，如果你修改了新對象的一個屬性值，並且這個屬性值是對象，那麼原始對象的相應屬性也會被修改。

```JS
Object.assign();
```


## 深拷貝 Deep Copy

> 當進行深拷貝時，無論對象的屬性值是基本數據類型還是對象，都會創建一個新的、完全獨立的複製。這意味著，如果你修改了新對象的一個屬性值，原始對象的相應屬性不會被修改。

```JS
JSON.parse(JSON.stringify(object));
```

