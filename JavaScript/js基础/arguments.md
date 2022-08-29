#arguments

---



```javascript
function fn() {
    console.log(arguments); // Arguments(4) [1, 2, 3, 4, callee: ƒ, Symbol(Symbol.iterator): ƒ]
}
fn(1, 2, 3, 4);
```
* `arguments`存储了传递过来的所有实参
* `arguments`是一个伪数组。具有`length`属性，按照索引的方式存储。但没有数组的一些方法。如`pop()`, `push()`等