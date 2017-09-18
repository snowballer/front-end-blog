# splice和slice间的区别

> 两者都属于数组方法，可用来截取数组元素

## 区别

- **splice**：

  语法：

  ```javascript

  array.splice(start)
  array.splice(start, deleteCount)
  //需要注意，第二个参数为0时，即deleteCount为0
  //之后参数添加到start位置后面
  array.splice(start, deleteCount, item1, item2, ...)

  ```

  说明：splice() 方法通过删除现有元素或添加新元素来更改一个数组的内容。

- **slice**：

  语法：

  ```javascript

    arr.slice()
    //[0,end]

    arr.slice(begin)
    //[begin,end]

    arr.slice(begin,end)
    //[begin,end)

  ```

  说明：slice() 方法返回的是浅拷贝原数组提取元素的新数组。

## 归纳

  slice属于immutable方法，不改变原数组；而splice会改变原数组，并且可以用于增加新元素。

## 案例

```javascript

var arr = [1, 2, 3, 4, 5];

//slice为纯函数
arr.slice(0, 3); // [1, 2, 3]

arr.slice(0, 3); // [1, 2, 3]

arr.slice(0, 3); // [1, 2, 3]

//splice具有副作用
arr.splice(0, 3); // [1, 2, 3]

arr.splice(0, 3); // [4, 5]

arr.slice(0, 3); // []

```

## 参考链接

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
