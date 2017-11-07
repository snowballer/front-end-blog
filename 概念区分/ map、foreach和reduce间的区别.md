#  map、foreach和reduce间的区别

> 三者之间的共同点：都属于数组迭代方法，都会对数组每个元素进行操作

## 区别

- **foreach**：

  语法：

  ```javascript

    array.forEach(callback(currentValue, index, array){
      //执行函数方法
    }[, thisArg])

  ```

  说明：forEach() 为每个数组元素执行callback函数；不像map() 或者reduce() ，它总是返回 undefined值，并且不可链式调用。

- **map**：

  语法：

  ```javascript

    let array = arr.map(function callback(currentValue, index, array) {
    // 返回一个新数组
    }[, thisArg])

  ```

  说明：map 不修改调用它的原数组本身，会返回一个新数组

- **reduce**：

  语法：

  ```javascript

    //accumulator在刚开始时为初始值，之后为上一次回调函数的返回值
    array.reduce(
      function(accumulator, currentValue, currentIndex, array), initialValue
    )

  ```

  说明：reduce() 方法对数组中的每个元素 (从左到右)应用一个函数进行累加器处理

## 归纳

- foreach进行遍历操作，每个元素执行一次回调函数

- map返回一个新数组，并将原数组和新数组间建立映射关联

- reduce对数组各元素进行累计运算

## 案例

关于reduce的实践：

&emsp;&emsp;reduce是进行累计操作的高阶函数，可以利用它实现读取出字符串中每个字符重复出现的次数

```javascript

var str = 'aabbbccccddd';

var result = str
  .split('')
  .reduce((r,i) => (r[i]++ || (r[i] = 1), r), {});
//r为回调函数返回值，初始值为{}
//i为数组中当前元素
//(param1, param2) => expression
// 等价于：(param1, param2) => { return expression; }
// || 逻辑或运算符从左至右执行，(r[i] = 1)很有必要
// (r[i] = 1)后的逗号运算符，只在最后一个表达式r被返回，其他的都只是被求值

console.log(result); //{ a: 2, b: 3, c: 4, d: 3 }

```

## 参考链接

- https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach

- https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map

- https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce

- https://www.zhihu.com/question/24927450

- https://segmentfault.com/q/1010000005070166
