#### 不要在选项property或回调上使用箭头函数

 不要在选项 property 或回调上使用[箭头函数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions)，

比如 `created: () => console.log(this.a)` 

或 `vm.$watch('a', newValue => this.myMethod())`。

因为箭头函数并没有 `this`，`this` 会作为变量一直向上级词法作用域查找，直至找到为止，

**经常导致 `Uncaught TypeError: Cannot read property of undefined` 或 `Uncaught TypeError: this.myMethod is not a function` 之类的错误。**



数据监听、编译模板、实例挂载

init初始化期间会执行beforeCreate  

init初始化结束就会执行created   换句话说 执行created 时一定已经初始化完成

