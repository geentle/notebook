# Node模块化

---

# Node中的模块

* 内置模块
* 自定义模块
* 第三方模块

### 加载模块

`require()`

```javascript
const fs = require('fs')							// 内置模块
const custom = require('./custom.js')	// 自定义模块，需指明路径，可以省略 .js 的后缀名
const moment = require('moment')			// 第三方模块
```
> 注意：使用`require()`方法可以加载模块时，会执行被加载的模块

### 模块的作用域

在自定义模块中定义的变量、方法等成员，**只能在当前模块内被访问**。这种模块级别的访问限制，叫做模块的作用域。

##### 向外共享模块作用域中的成员

* `module`对象，它存储了和当前模块有关的信息。
* `module.exports`对象：在自定义模块中，可以使用`module.exports`对象，将模块内的成员共享出去，供外界使用。外界使用`require()`方法导入自定义模块时，得到的就是`module.exports`所指向的对象
* `exports`对象：`exports`和`module.exports`指向的是同一个对象

> 注意：`require()`引入模块时，得到的永远是`module.exports`指向的对象