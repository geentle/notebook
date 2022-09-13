# for-in 和 for-of

---

## for-in

* 为了遍历普通对象设计的
* 可枚举性决定一个属性是否会被`for-in`遍历到
* 作用于数组的`for-in`循环除了遍历数组元素以外,还会遍历自定义属性；并且原型链上的属性也会被遍历到

> 注意：如果想原型链上的属性被遍历到，可以使用`hasOwnProperty(propertyName)`方法。该方法用来检测属性是否为对象的自有属性，如果是，返回true，否者false; 参数propertyName指要检测的属性名；

## for-of

* ES6引入的
* 允许遍历**可迭代的数据结构**，如 Arrays（数组）、Strings（字符串）、Maps（映射）、Sets（集合）等
* 不能直接用来遍历普通对象，要通过`Object.keys()`搭配使用

```js
let person = {
    name: 'zs',
    age: 18,
    address: 'scau'
}
for(let item of Object.keys(person)) {
    console.log(item, person[item]);
}
```
```text
name zs
age 18
address scau
```

## 对比

* `for-in`遍历时拿到的是key；`for-of`遍历时拿到的是value；

## 属性的可枚举性
属性的枚举性会影响以下三个函数的结果

* for in （不可枚举的属性不会被遍历出来）
* Object.keys（只返回对象本身具有的可枚举的属性）
* JSON.stringify() （此方法也只读取对象本身可枚举属性，并序列化为JSON字符串）
* Object.assign() （此方法也是复制自身可枚举的属性，进行浅拷贝）