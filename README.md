# react-hook

## why



## what
Hook 让你在不编写 class 的情况下使用 state 以及生命周期等特性的函数；

react 官方不推荐把已有的组件全部重写为 hook，推荐渐进式地使用 hook

## how
### State Hook

#### useState 简单的栗子

``` jsx
import React, { useState } from 'react';

function Example() {
  // 声明一个叫 “count” 的 state 变量。
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

#### useState 做了什么？

1. 通过 useState 给组件添加了一些内部 state， React 会在重复渲染时保留这个 state；
2. 返回对值：当前的状态和一个让你更新它的函数，可在事件处理函数调用这个更新函数，类似 ```this.setState```, 但是 **它不会把新的 state 和旧的 state 做合并** ；
3. useState 只有一个参数，用于初始化 **state**, 不一定是对象， 可以是任何类型的值；


> 【新的组件形态】之前我们将通过 function 创建的函数组件称为 **无状态组件** ，但现在我们引入了 React state 的能力，在名称上需要更新为 **函数组件** 更为合适，以免概念上混淆，那么就存在 **状态组件、无状态组件、函数组件** 三种情况。

#### 注意
* hook 在 class 中不起作用；


#### 对比下在 class 的写法
```jsx
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    }
  }
  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me
        </button>
      </div>
    )
  }
}
```

差别：
* 读取不再需要通过 **this.state.count** ，而是直接 **count** 
* 更新 state 不再通过 **this.setState**, 而是通过 **setCount** 或者其他你命名的函数名如 **doItNow**，但为了可读性，建议格式为 "**set + state名称**"

### Effect Hook
#### 是什么？
我们之前已经在 React 组件中执行过数据获取、订阅或者手动修改 DOM，我们统一把这些操作成为**副作用**，effect hook 就是给函数组件增加操作副作用的能力，和 class 组件中的 ```compnonentDidMount, componentDidUpdate, componentWillUnmount``` 具有相同的用途，只不过合并为一个 api。

听起来貌似不太靠谱，一个 api 怎么能够满足之前三个生命周期的场景？组件加载、更新、卸载做的事情是不一样的。

副作用有两种：**需要清除的和不需要清除的**

#### 无需清除的副作用（effect）




## 参考
* [react hook 官方介绍](https://zh-hans.reactjs.org/docs/hooks-intro.html)
* [react-use github](https://github.com/streamich/react-use)
* [react hook FAQ](https://zh-hans.reactjs.org/docs/hooks-faq.html#how-does-react-associate-hook-calls-with-components)
