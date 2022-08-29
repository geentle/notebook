# BOM

---

### BOM概述

浏览器对象模型

浏览器厂商各自在浏览器上定义的，兼容性比较差

window是浏览器对象的顶级对象。

window是一个全局对象。全局作用域中的变量、函数都会变成window对象的属性和方法。

### 窗口加载事件

`window.onload`: 页面完全加载完成会触发该事件。只能写一次，以最后一个为准。

实例
```javascript
window.onload = function () {};
// 也可以这么写
window.addEventListener('load', function (){});
// 只要加载完DOM就执行则用
document.addEventListener('DOMContentLoaded', function (){});
```

### 调整窗口大小

`resize`事件: 窗口大小发生变化就会触发事件。可以用于完成一些响应式布局

```javascript
window.addEventListener('resize', function (){});
```

### 定时器

* `window.setTimeout(callback, time)`: 到时间就调用一次
  * 停止定时器: `window.clearTimeout(timeoutID)`
* `window.setInterval(callback, time)`: 每个一段时间，重复调用
  * `window.clearInterval(intervalID)`

两个方法都属于window对象。

定时器里的`this`指向`window`。

### JS执行队列

JavaScript是单线程的。所以的任务都要排队。

##### 同步和异步
HTML5提出 Web Worker 标准，允许 JavaScript 脚本创建多个线程。于是出现了同步和异步。

###### 同步
前一个任务结束后再执行后一个任务。

###### 异步
允许多个任务同时进行。

###### 同步和异步执行机制

同步任务在主线程上执行，形成一个执行栈。

异步任务放在任务队列(消息队列)上

1. 先执行主线程执行栈上的任务，如果有异步任务则放在消息队列中，继续执行主线程执行栈上的同步任务。
2. 执行栈上任务执行完毕后，在消息队列中把异步任务放到执行栈末尾，逐步执行异步任务。

![](C:\Users\93932\Pictures\Saved Pictures\js\JS任务执行机制.png)JS执行机制

##### location对象
window对象给我们提供了一个location属性用于获取或设置窗体的URL，并且可以用于解析URL。

location对象属性
* location.href
* location.host
* location.port
* location.pathname
* location.search
* location.hash
location对象方法
* assign(): 重定向
* replace()
* reload()

##### navigator对象
navigator对象包含有关浏览器的信息，有很多属性。比如userAgent属性可以返回user-agent头部的值。

##### history对象
window对象给我们提供了一个history对象，与浏览器历史记录进行交互



