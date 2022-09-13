#DOM

---

## 获取元素

* 根据ID：`document.getElementByID()`
* 根据标签名获取：`getElementsByTagName()`
* 通过HTML5新增的方法获取：
  * `document.getElementByClassName()`
  * `document.querySelector()`  返回的是第一个符合选择器的元素
  * `document.querySelectorAll()`  返回的是所有符合选择器的元素
* 特殊元素获取
  * 获取body：`document.body`
  * 获取html：`document.documentElement`

## 事件

### 事件基础   
#### 操作元素
* 修改元素内容
  * `element.innerText`: 不识别HTML标签
  * `element.innerHTML`: 识别HTML标签
* 修改元素属性
  * `element.attribute`：直接赋值
* 修改样式属性
  * `element.style.xxx`：直接赋值
* 获得自定义属性
  * `element.getAttribute(attributeName)`
* 设置自定义属性
  * `element.setAttribute(attributeName, value)`
* H5自定义属性
  * `data-`开头，比如`data-index="1"`

#### 节点操作
* 最近的父节点：`element.parentNode`
* 所有子节点(包括元素节点和文本节点)：`element.childNodes`
* 所有子节点中的元素节点：`element.children`
* 获取第一个孩子：`element.firstChild`
* 获取最后一个孩子：`element.lastChild`
* 获取第一个子元素节点：`element.firstElementChild`
* 获取最后一个子元素节点：`element.lastElementChild`
* 获取上一个兄弟节点：`element.previousSibling`
* 获取下一个兄弟节点：`element.nextSibling`
* 获取上一个兄弟元素节点：`element.previousElementSibling`
* 获取下一个兄弟元素结点：`element.nextElementSibling`
* 创建节点：`document.createElement()`
* 添加节点：`node.appendChild(newNode)`、`node.insertBefore(newNode)`
* 删除节点：`node.removeChild(child)`
* 复制节点：`node.cloneNode()`
* 创建元素：`document.write()`

###### write、innerHTML和createElement效率对比
* `document.write()`
* `element.innerHTML()`
* `document.createElement()`
  
`document.write()`是直接将内容写入页面内容流，但是文档流执行完毕，则它到导致页面全部重绘
`element.innerHTML()`是将内容写入某个DOM节点，不会导致页面全部重绘

`element.innerHTML()`创建多个元素效率更高。


###事件高级

注册事件
* `addEventListener()`
* `onclick`等属性

删除事件
* 给`onclick`等属性赋予`null`
* `removeEvenListener()`

####DOM事件流

DOM事件流分为3个阶段
1.捕获阶段 document -> html -> body -> father -> son
2.当前目标阶段
3.冒泡阶段 son -> father -> body -> html -> document

####阻止事件默认行为
`event.preventDefault()`

作用：比如让 a 标签不跳转

####阻止冒泡

`event.stopPropagation()`

####事件委托(事件代理、事件委派)

事件委托原理：不是每个子节点单独设置事件监听器，而是事件监听器设置在其**父节点**上，然后利用**冒泡原理**影响设置每个子节点。

事件委托的作用：只操作了一次DOM，提高了程序的性能。

####常用的鼠标事件
* onclick: 鼠标左键点击触发
* onmouseover: 鼠标经过触发
* onmouseout: 鼠标离开触发
* onfocus: 获得鼠标焦点触发
* onblur: 失去鼠标焦点触发

######鼠标事件对象

用`console.log(e)`可以看到
```javascript
let box = document.getElementById("demo");
box.addEventListener('click', function (e){
    console.log(e);
})
```

######mouseenter和mouseover的区别
* 当鼠标移动到元素上会触发事件
* mouseover鼠标经过自身盒子会触发，经过子盒子还会触发。mouseenter只会经过自身盒子触发。

####常用的键盘事件
* onkeyup: 某个键盘按键被松开时触发
* onkeydown: 某个键盘按键被按下时触发
* onkeypress: 某个键盘按键被按下时触发。但不识别功能键，比如ctrl、shift、箭头等。

######键盘事件对象
```javascript
document.addEventListener('keyup', (e) => console.log(e));
```




