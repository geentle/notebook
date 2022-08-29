#Hoisting

---

在 JavaScript 中，可以在使用变量之后对其进行声明。
换句话说，可以在声明变量之前使用它。
**例子 1** 与 **例子 2** 的结果相同：

例子1
```javascript
x = 5; // 把 5 赋值给 x
 
elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x;                     // 在元素中显示 x

var x; // 声明 x
```

例子2
```javascript
var x; // 声明 x
x = 5; // 把 5 赋值给 x

elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x;                     // 在元素中显示 x
```

###`let` 和 `const` 关键字

用 `let` 或 `const` 声明的变量和常量不会被提升！