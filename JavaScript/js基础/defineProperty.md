#defineProperty方法

---

`Object.defineProperty(obj, prop, descriptor)`给对象定义新属性或修改原有属性

- obj: 必需。目标对象
- prop: 必需。需定义或修改的属性的名字
- descriptor: 必需。目标属性所拥有的特性

```javascript
let obj = {
    id: 1,
    name: 'andy',
    price: 1999,
};
// 新增属性
Object.defineProperty(obj, 'num', {
    value: 1000,
});
// 修改属性的值
Object.defineProperty(obj, 'price', {
    value: 19.9,
});
// 修改属性的值
Object.defineProperty(obj, 'id', {
    writable: false,
});
console.log(obj);
```

第三个参数`descriptor`接受一个对象，对象中可以包含如下成员
- value: 设置属性的值。默认为`undefined`。
- writable: 值是否可以重写。布尔值，默认为false。
- enumerable: 目标属性是否可以枚举。布尔值，默认为false。为false时不允许遍历
- configurable: 目标属性是否可以被删除是否可以再次修改特性(再次修改特性指不能再用defineProperty设置他的特性)。布尔值，默认为false。