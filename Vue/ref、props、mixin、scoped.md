# ref、pros、mixin、scoped

---

### ref属性
* 用来给元素或子组件注册引用信息
* 应用在`html`标签上获取的是真是DOM元素；应用在足见标签上获取的是组件实例对象(VueComponent)
* 使用方式：
  * 打标识：`<div ref="xxx">...</div>` 或 `<Component ref="xxx"> ... </Component>`
  * 获取：`this.$refs.xxx`

### props配置项

实现组件间通信。让组件接受外部传来的值

##### 传递数据：

`<Demo name="xxx"/>`

##### 接收数据：

第一种方式(只接收)：
`props: ['name']`

第二种方式(限制类型):
```javascript
props:{
    name: Number
}
```
第三种方式(限制类型、限制必要性、指定默认值)
```javascript
props: {
    name: {
        type: String, // 类型
        required: true, // 必要性
        default: '老王' // 默认值
    }
}
```

> `props`是只读的，`Vue`底层会监测你对`props`的修改，如果进行了修改，就会发出警告。

### mixin

混入。

##### 功能
可以把多个组件公用的配置提取成一个混入对象。

##### 使用方式：
第一步，定义混合
```javascript
{
    data() { return {...} },
    methods: {...}
}
```
第二步，使用混入

* 全局混入： `Vue.mixin(xxx)`
* 局部混入：`mixins:[xxx, xxx]`

##### 选项合并

当组件和混入对象含有同名选项时，这些选项将以恰当的方式进行“合并”。

1. 数据对象在内部会进行递归合并，并在发生冲突时以组件数据优先。
2. 同名钩子函数将合并为一个数组，因此都将被调用。另外，混入对象的钩子将在组件自身钩子之前调用。
3. 值为对象的选项，例如`methods`、`components`和directives，将被合并为同一个对象。两个对象键名冲突时，取组件对象的键值对。

### scoped

##### 作用
让样式在局部生效，防止冲突

##### 用法
```vue
<style scoped>
```

### lang

##### 作用
指定编写style的语言

##### 用法
```vue
<style lang="less">  
```