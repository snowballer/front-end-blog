# FP

> 函数式编程（Functional Programming，简称FP），和OOP(Object-oriented Programming)一样，是一种编程范式。FP简单点说，核心就是用函数组合的方式（Lambda演算）来描述计算过程，从而实现输入与输出的功能。

## 特性

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

## JS函数式进程
   
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

## 函数式理论

- 纯函数（pure function）

  无副作用：只要函数的输入值（参数）确定，则函数的输出值（返回值）固定

  示例代码：https://jsbin.com/cipozix/edit?js,console

- 高阶函数 (higher-order function)

  至少满足下列条件之一的函数：

  &nbsp;&nbsp;1.接受函数作为参数
      
  &nbsp;&nbsp;2.返回一个函数

  示例代码：https://jsbin.com/batoti/edit?js,console
  
- 柯里化（currying）
  
  把接受多个参数的原函数变换成只接受一个单一参数的原函数

  柯里化的实质是原函数自身返回一个新函数来接受第二个参数，依次返回并接受剩余参数

  在函数组合时，柯里化能将关注的重点聚焦于函数本身，而不是冗余的数据参数，从而能够写出 Pointfree（无参数）风格的函数。

  示例代码：https://jsbin.com/yefipos/edit?js,console

- 组合 (compose)

  函数组合即把多个函数组合起来变成一个函数

  函数组合建立起一种声明式数据流，增强了代码可读性，使关注点侧重于组合后的函数本身，而非组合的过程

  compose实现函数从右至左组合，pipe实现函数从左至右组合

  示例代码：https://jsbin.com/movihut/edit?js,console

## 函数式应用

- 数据交互（ajax）

  前后端数据交互时，经常需要对数据进行再处理，而此类数据结构操作使用列表操作函数（map、filter、reduce等）进行函数组合会让数据流更加清晰

  示例代码：https://jsbin.com/ganinuf/edit?js,console

- 高阶组件（HOC）

  顾名思义，跟高阶函数类似，高阶组件接受组件为参数，并返回一个组件

  示例代码：React高阶组件demo

- 状态管理 (redux)
  
  
  