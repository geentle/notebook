# 理解Vuex

---

### Vue状态管理

> 由于状态零散地分布在许多组件和组件之间的交互中，大型应用复杂度也经常逐渐增长。为了解决这个问题，Vue 提供 vuex

![Vuex](../img/vuex.png)

### 基础API

配置项

`actions`

`mutations`

`state`

`getters`


### mapState、mapActions、mapMutations、mapGetters

* `mapState`：用于映射`state`中的数据为计算属性

```javascript
computed: {
  	// 借助mapState生成计算属性：sum、school、subject（对象写法一）
    ...mapState({sum:'sum',school:'school',subject:'subject'}),

  	// 借助mapState生成计算属性：sum、school、subject（数组写法二）
  	...mapState(['sum','school','subject']),
},
```

* `mapGetters`：用于映射`getters`中的数据为计算属性

```javascript
computed: {
    //借助mapGetters生成计算属性：bigSum（对象写法一）
    ...mapGetters({bigSum:'bigSum'}),

    //借助mapGetters生成计算属性：bigSum（数组写法二）
    ...mapGetters(['bigSum'])
}.
```

`mapActions`：用于帮助我们生成与`actions`对话的方法，即包含`$store.dispatch(xxx)`的函数

```javascript
methods:{
    //靠mapActions生成：incrementOdd、incrementWait（对象形式）
    ...mapActions({incrementOdd:'jiaOdd',incrementWait:'jiaWait'})

    //靠mapActions生成：incrementOdd、incrementWait（数组形式）
    ...mapActions(['jiaOdd','jiaWait'])
}
```

`mapMutations`：用于帮助我们生成与`mutations`对话的方法，即包含`$store.commit(xxx)`的函数
```javascript
methods:{
    //靠mapActions生成：increment、decrement（对象形式）
    ...mapMutations({increment:'JIA',decrement:'JIAN'}),
    
    //靠mapMutations生成：JIA、JIAN（对象形式）
    ...mapMutations(['JIA','JIAN']),
}
```

> 注意：`mapActions`与`mapMutations`使用时，若需要传递参数需要在模板中绑定事件时传递好参数，否则接收到的参数是事件对象。