# 字符串的replace方法

---

### 定义和基本用法

replace() 方法用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。

##### 语法

`string.replace(searchvalue,newvalue)`

实例

```javascript
var str="Mr Blue has a blue house and a blue car";
var n=str.replace(/blue/g,"red");
```
结果
```text
Mr Blue has a red house and a red car
```

### 输入的第二个参数可以是回调函数

##### 回调函数的形式
```javascript
(sub, index, str) => {
    ...
}
```
* `sub`是根据正则表达式扫描到的字符串切片
* `index`是遍历时的索引
* `str`是原字符串

##### 执行过程

遍历所有符合正则表达式的字符串切片，把切片内容替换成回调函数的返回值。

实例

```javascript
let s = 'aba22abas'
let s2 = s.replace(/[ab]/g, (sub, index, str) => {
    console.log(index, sub, str)
    if (sub === 'a') {
        return 'A'
    } else if (sub === 'b') {
        return 'B'
    } else {
        return '@'
    }
})
console.log(s2) // ABA22ABAs
```