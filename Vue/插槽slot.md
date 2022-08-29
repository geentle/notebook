# 插槽slot

---

>  让父组件可以向子组件指定位置插入`html`结构，也是组件间通信的一种方式


### 默认插槽

```vue
父组件中：
<Category>
    <div>html结构1</div>
</Category>

子组件中：Category
<template>
    <div>
        <!-- 定义插槽 -->
        <slot>插槽默认内容...</slot>
    </div>
</template>
```

### 具名插槽
父组件中可以指明放入子组件的插槽，但子组件要定义插槽名。
`name="slotName"`，如果是`template`可以写成`"v-slot:slotName"`

```vue
父组件中：
<Category>
    <template slot="center">
        <div>html结构1</div>
    </template>

    <template v-slot:footer>
        <div>html结构2</div>
    </template>
</Category>
子组件中：Category
<template>
    <div>
        <!-- 定义插槽 -->
        <slot name="center">插槽默认内容...</slot>
        <slot name="footer">插槽默认内容...</slot>
    </div>
</template>
```

### 作用域插槽   

作用于插槽的数据在子组件自身，而父组件决定结构。

`scope`用于接收子组件的数据。

```vue
父组件中：
<Category>
    <template scope="scopeData">
        <!-- 生成的是ul列表 -->
        <ul>
            <li v-for="g in scopeData.games" :key="g">{{g}}</li>
        </ul>
    </template>
</Category>

<Category>
    <template slot-scope="scopeData">
        <!-- 生成的是h4标题 -->
        <h4 v-for="g in scopeData.games" :key="g">{{g}}</h4>
    </template>
</Category>
子组件中：
<template>
    <div>
        <slot :games="games"></slot>
    </div>
</template>

<script>
    export default {
        name:'Category',
        props:['title'],
        //数据在子组件自身
        data() {
            return {
                games:['红色警戒','穿越火线','劲舞团','超级玛丽']
            }
        },
    }
</script>
```

> 关于**样式**，既可以写在父组件，解析后放入子组件插槽；也可以放在子组件中，传入给子组件再解析