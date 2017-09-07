#BrowserRouter组件
正如我们上一个视频里看到的那样。当用户点击‘back’按钮，页面只是刷新了一下，显示的内容还是点击之前的内容，这种体验是非常糟糕的。当我们更新位置的时候，我们同样可以利用JavaScript来更新我们的应用。这时就需要React Router了。

#安装React Router
首先安装[react-router-dom](https://www.npmjs.com/package/react-router-dom)
```
**[terminal]
npm install --save react-router-dom
```
{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-5ManagingAppLocation-3-1.mp4{% endvideo %}
[这里是视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/3ac98594059c5c245c6032f1484ee0953331b43f)

#BrowserRouter
首先看一下BrowserRouter这个组件

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-5ManagingAppLocation-3-2.mp4{% endvideo %}


{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-5ManagingAppLocation-3-3.mp4{% endvideo %}
[视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/544d6aff26d6e35b40bd17a633cf7c21c5eb4969)

React Router里比较好的地方是所有的东西都是组件。这就使得使用起来非常赞，同样深入代码非常便捷。下面看一下BrowserRouter内部的结构。

```js
**[terminal]
class BrowserRouter extends React.Component {
  static propTypes = {
    basename: PropTypes.string,
    forceRefresh: PropTypes.bool,
    getUserConfirmation: PropTypes.func,
    keyLength: PropTypes.number,
    children: PropTypes.node
  }

  history = createHistory(this.props)

  render() {
    return <Router history={this.history} children={this.props.children}  />
  }
}
```
当使用`BrowserRouter`的时候，实际上你做的是渲染一个`Router`组件，并且给它传递一个`history`的prop。`history`来自[history](https://github.com/ReactTraining/history)库。这个库的主要目的就是消除各种环境的差异，并提供一个最小的API，可以让你管理历史堆栈，导航，确认导航，并在会话之间保持状态。

简言之，就是当你使用`BrowserRouter`的时候，你就创建了一个`history`对象，它将监听URL的变化，确保应用理解这些变化。


#小结
总之，为了使React Router正确的工作，你需要将整个App嵌入到`BrowserRouter`组件里。同样，`BrowserRouter`包含着history库，会让你的app可以监听URL的变化

#延伸阅读
- [history](https://github.com/reacttraining/history)

