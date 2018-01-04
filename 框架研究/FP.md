# FP

> 函数式编程（Functional Programming，简称FP），和OOP(Object-oriented Programming)一样，是一种编程范式。FP简单点说，核心就是用函数组合的方式（Lambda演算）来描述计算过程，从而实现输入与输出的功能。

## 核心特点

- 函数是一等公民（First-class Function）  
  
  函数和其它数据类型处于平等地位，可以把函数赋值给其他变量，也可以作为参数传入另一个函数，或者作为别的函数的返回值。


- 无副作用（No Side Effects）

  只要函数的输入值（参数）确定，则函数的输出值（返回值）固定

- 无状态（Stateless）

  在闭包的情况下，函数的返回值与外部变量无关联性

- 不可变数据 (Immutable Data)
  
  在函数式编程中，state是不可以改变的，如果要改变state，需要浅拷贝再进行修改。

- 必须有返回值（Return）
  
  函数应该接收输入值，并且返回输出值

## JS函数式编程
   
在ES6和Babel普及前，JS对函数式编程范式支持度并不好。随着ES6的普及，ES6中的很多新特性提升了JS对函数式编程范式支持度。

函数体：

- 剩余参数

- 箭头函数

- 解构赋值

示例代码：https://jsbin.com/fosopeq/edit?js,console

数组：

- map

- filter

- reduce

示例代码：https://jsbin.com/mabeju/edit?js,console

对象：

- Object.assign

- 扩展运算符

示例代码：https://jsbin.com/xucukoc/edit?js,console