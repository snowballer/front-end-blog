# apply、call和bind间的区别

> 三者之间的共同点：都可以改变函数体内this的指向

## 区别

- **apply**：

    语法：fun.apply(thisArg, [argsArray])

    说明：apply()方法接受的是一个包含多个参数的数组

- **call**：

    语法：fun.call(thisArg[, arg1[, arg2[, ...]]])

    说明：call()方法接受的是若干个参数的列表

- **bind**：

    语法：fun.bind(thisArg[, arg1[, arg2[, ...]]])

    说明：bind()方法会创建一个新的绑定函数，当新函数被调用时 this 值绑定到 bind() 的第一个参数，该参数不能被重写。

## 归纳

bind与apply、call最大的区别就是：bind不会立即调用，apply和call会立即调用

## 案例

React里bind的实践：

&emsp;&emsp;react中没绑定this的指向的话,默认为null，而非window

```javascript
//jsx中绑定
<div onClick={this.handleClick.bind(this)}>demo</div>

//构造器内绑定
constructor(props){
  super(props);
  this.handleClick=this.handleClick.bind(this)
}

//利用闭包绑定,箭头函数的this总是指向词法作用域，也就是外层调用者
//因为内部为匿名函数会导致组件更新时重渲染，影响性能
<div onClick={()=>this.handleClick}>demo</div>
```

## 参考链接

- https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind

- http://blog.csdn.net/a_dangdang/article/details/50986168

- https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001438565969057627e5435793645b7acaee3b6869d1374000
