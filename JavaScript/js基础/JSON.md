#JSON

---

JSON: **J**ava**S**cript **O**bject **N**otation

###把 JSON 文本转换为 JavaScript 对象

使用`JSON.parse()`方法
```javascript
var text = '{ "employees" : [' +
'{ "firstName":"Bill" , "lastName":"Gates" },' +
'{ "firstName":"Steve" , "lastName":"Jobs" },' +
'{ "firstName":"Alan" , "lastName":"Turing" } ]}';

var obj = JSON.parse(text);
```

###把对象转为JSON字符串
使用`JSON.stringify()`方法
```javascript
const person = {
    name: "Bill",
    age: 19,
    city: "Seattle"
};

let myString = JSON.stringify(person);
```