# vuex模块化

---

> 目的: 让代码更好维护，解决命名冲突

为了解决不同模块命名冲突问题，需要将不同模块配置`namespaced: true`

 ```javascript
const countAbout = {
  namespaced: true,	// 开启命名空间
  state: {x:1},
  mutations: { ... },
  actions: { ... },
  getters: {
    bigSum(state){ return state.sum * 10 }
  }
}

const personAbout = {
  namespaced: true,	// 开启命名空间
  state: { ... },
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    countAbout,
    personAbout
  }
})
 ```

 开启命名空间后，组件读取数据会有所变化，需要指明是哪个模块的数据

 * 读取`state`数据

```javascript
// 方式一：自己直接读取
this.$store.state.personAbout.personList
// 方式二：借助mapState读取：
...mapState('countAbout',['sum','school','subject']),
```

* 读取`getters`的数据

```javascript
//方式一：自己直接读取
this.$store.getters['personAbout/firstPersonName']
//方式二：借助mapGetters读取：
...mapGetters('countAbout',['bigSum'])
```

* 调用`dispatch`

```javascript
//方式一：自己直接dispatch
this.$store.dispatch('personAbout/addPersonWang',person)
//方式二：借助mapActions：
...mapActions('countAbout',{incrementOdd:'jiaOdd',incrementWait:'jiaWait'})
```

* 调用`commit`

```javascript
//方式一：自己直接commit
this.$store.commit('personAbout/ADD_PERSON',person)
//方式二：借助mapMutations：
...mapMutations('countAbout',{increment:'JIA',decrement:'JIAN'}),
```