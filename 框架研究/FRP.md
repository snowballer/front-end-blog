# FRP

> FRP（Functional Reactive Programming）是一种面向数据流和变化传播的编程范式。FRP简单点说，核心就是用静态或动态的数据流组合的方式，自动实现输入与输出的功能。

## 引言

![](../imgs/Vue-MVVM.png)

如上图所示，在MVVM类框架中，双向绑定实现了数据与视图同步。当然谈到双向绑定，一般会提到发布-订阅模式和观察者模式，当然这两种设计模式本身蕴含了响应式编程思想。

在实际开发中，经常使用的Vue的computed和Webpack的hot reload也是此类思想的体现。

## 核心概念

- 事件驱动 

  事件驱动往往是异步的,而异步处理在数据交互和界面交互中非常普遍。

  示例代码：https://jsbin.com/ferujec/edit?html,js,console,output

- 可扩展性

  数据流可以通过类似函数组合的方式来进行动态调节。

- 容错性

  类似于Promise的catch及try/catch，可以捕获错误

- 响应式

  当Observable（被观察者）变化时，会通知Observer（观察者）

## Rx/js库

- Observable

- Observer

- Operators 

- Subject

- Scheduler 
