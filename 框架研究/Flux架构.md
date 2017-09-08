# Flux 架构

> Flux是Facebook用来构建客户端Web应用的应用架构。它利用单向数据流的方式来组合React中的视图组件。

## 单向数据流

- 极简流程图：

![](../imgs/flux-1.png)

- 考虑到项目中，用户交互也会产生一个新Action，流程图应如下：

![](../imgs/flux-2.png)

- 考虑到项目中，Action Creators可能会向外部请求数据，完整流程图应如下：

![](../imgs/flux-3.png)

## 核心概念

- Views 即 React 组件。它们负责渲染界面，捕获用户事件，从 Stores 获取数据。

- Stores 用于管理数据。 一个 Store 管理一个区域的数据，当数据变化时它负责通知 Views。

- Dispatcher 用于接收新数据然后传递给 Stores，Stores 更新数据并通知 Views。

- Actions 是传递给 Dispatcher 的对象，包含新数据和 Action Type。

- Action Types 指定了可以创建哪些 Actions，Stores 只会更新特定 Action Type 的 Actions 触发的数据。

- Action Creators 是 Actions 的创建者，并将Actions传递给 Dispatcher 或 Web Utils。

- Web Utils 是用于与外部 API 通信的对象。例如 Actions Creator 可能需要从服务器请求数据。
