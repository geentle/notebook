#defineProperty

---
> 给对象定义属性
> 
> `Object.defineProperty(obj,property,descriptor)`

* 参数1：obj
  * 绑定属性的目标对象
* 参数二：property
  * 绑定的属性名
* 参数三：descriptor
  * 属性描述（配置），且此参数本身为一个对象
    * `value`: 设置属性默认值 
    * `writable`: 设置属性是否能够修改 
    * `enumerable`: 设置属性是否可以枚举，即是否允许遍历 
    * `configurable`: 设置属性是否可以删除或编辑 
    * `get`: 获取属性的值
    * `set`: 设置属性的值
