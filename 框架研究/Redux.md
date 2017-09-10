# Redux

> Redux 由 Flux 演变而来，并且引入了大量函数式编程的理念，提供可预测化的状态管理。

## 单向数据流

不同于Flux架构，Redux中没有dispatcher这个概念，并且Redux设想你永远不会变动你的数据，你应该在reducer中返回新的对象来作为应用的新状态。但是它们都可以用(state, action) => newState来表述其核心思想，所以Redux可以被看成是Flux思想的一种实现，但是在细节上会有一些差异。

![](../imgs/redux.png)

## 流程图

![](../imgs/reduxFlow.png)
