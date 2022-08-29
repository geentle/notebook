# Vue.$nextTick

---

* 语法：`this.$nextTick(callback)`
* 作用：在**下一次DOM更新结束后**执行其指定的回调。
* 当改变数据后，要基于更新后的新DOM进行某些操作时，在`this.$nextTick(callback)`的回调函数中执行操作。