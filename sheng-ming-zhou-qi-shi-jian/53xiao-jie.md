#小结
生命周期事件是一些特殊的方法，这些方法允许我们在一个组件里的不同的生命节点处运行特定的代码。有很多生命周期的事件函数，这里我们把他们分成三类

#添加进DOM里面的事件
- `constructor()`
- `componentWillMount()`
- `render()`
- `componentDidMount()`

#重新渲染
- `componentWillReceiveProps()`
- `shouldComponentUpdate()`
- `componentWillUpdate()`
- `render()`
- `componentDidUpdate()`

#从DOM中移除
- `componentWillUnmount()`

下面这张图很清楚的说明了这些时间发生的时间节点

![](/assets/react-lifecycle.png)
从左上角开始，当ReactDOM渲染组件的时候，依次发生

从图中可以看出，有很多不同的生命周期事件。但是常用的事件是这几个:`componentDidMount()`, `componentWillMount()`, `componentWillUnmount()`, and `componentWillReceiveProps()`。

#延伸阅读
- [componentWillMount()](https://facebook.github.io/react/docs/react-component.html#componentwillmount) from the React Docs
- [componentDidMount()](https://facebook.github.io/react/docs/react-component.html#componentdidmount) from the React Docs
- [componentWillUnmount()](https://facebook.github.io/react/docs/react-component.html#componentwillunmount) from the React Docs
- [componentWillReceiveProps()](https://facebook.github.io/react/docs/react-component.html#componentwillreceiveprops) from the React Docs
- [Component Lifecycles](https://facebook.github.io/react/docs/react-component.html#the-component-lifecycle) from the React Docs
