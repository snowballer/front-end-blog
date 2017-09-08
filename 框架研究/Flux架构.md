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

## 概念解析

- Action：包含Action Type以及应用送往store(存储)的信息载荷(payload,也可称为有效信息)

  Action具有固定格式的，即FSA, 全称为Flux Standard Action，格式如下:

  ```javascript

  {
    type: 'ADD_TODO',
    payload: {
      text: 'Do something'  
    }
  }

  ```
- Action Type : Action中的type , 如下：

  ```javascript

  {
    type: 'COMPLETE_TODO', //action type
    payload: {
      text: 'Do something'  
    }
  }

  ```

- Action Creator ：是一种辅助创建Action的函数，类似工厂模式，传入参数生成对应的Action ，如下所示：

  ```javascript

  let addItemAction = (text = 'First thing')=>{  
    return{      
      type:'ADD_ITEM',
      text
    }
  }

  ```

- Dispatcher : 将Action和Store联系在一起，Action中通过Dispatcher.dispatch({actionType, payload})来分发事件，Store中通过Dispatcher.register(function(action))来响应其注册的Action。注意，Dispatcher 只能有一个，而且是全局的。

  ```javascript

  //引用模块
  var Dispatcher = require('flux').Dispatcher;

  // 分发事件，即创建Action
  var Actions = {
    Createor: function (text) {
      Dispatcher.dispatch({
        actionType: 'ADD_ITEM',
        text: text
      });
    }
  };

  // Store响应Action
  Dispatcher.register(function (action) {
    switch(action.actionType) {
      case 'ADD_ITEM':
        Store.handlerAddItem(action.text); //回调函数，用于存储数据到Store
        Store.emitChange();//回调函数，通知数据改变
        break;
    }
  })

  ```

- Stores : 保存数据及当数据变动时通知视图更新(pub/sub模式)

  ```javascript
  //引用node的EventEmitter模块
  var EventEmitter = require('events').EventEmitter;

  //Object.assign() 方法用于将所有可枚举的属性的值从一个或多个源对象复制到目标对象
  var Store = Object.assign({},EventEmitter.prototype, {

    items: [],

    getAll: function () {
      return this.items;
    },

    //添加数据
    handlerAddItem: function (text) {
      this.items.push(text);
    },

    //通知数据变化
    emitChange: function () {
      this.emit('change');
    },

    addChangeListener: function(callback) {
      this.addEventListener('change', callback);
    },

    removeChangeListener: function(callback) {
      this.removeEventListener('change', callback);
    }
  });

  ```

- Views : 视图层及数据变动时重新渲染视图

  ```javascript

  import React,{Component} from 'react';

  export default class Class extends Component {

    constructor(props) {
      super(props);
      this.state = {items: Store.getAll()};
    }

    //componentDidMount生命周期内添加监听事件
    componentDidMount: function() {
      Store.addChangeListener(this.storeChange);
    }

    //componentWillUnmount生命周期内移除监听事件
    componentWillUnmount: function() {
      Store.removeChangeListener(this.storeChange);
    }

    //当数据发生改变时，调用setState进行组件重新渲染
    storeChange: function () {
      this.setState({
        items: Store.getAll()
      });
    }

    addItem: function () {
      Actions.addItem('new item');
    }

    render() {
      return (
        <View
          items={this.state.items}
          onClick={this.addItem}
        />;
        );
    }
  }

  ```
