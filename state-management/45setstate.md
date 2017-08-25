#更新state
更新state需要用setState方法，而不能直接强制赋值
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/TU1GGjogtbo.mp4{% endvideo %}
下面我们看一下具体怎么通过setState函数来修改state
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/d3UNPA863f4.mp4{% endvideo %}
[这是视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/f794f553e4937f6b2afaab2acdb14c623d8eb8c1)

#State是如何设置的

之前我们看到过我们是如何在初始化的时候定义一个组件的state的。state是映反映了最终渲染出来的信息，组件可以在生命周期里通过`this.setState()`来更新自己的state，。每一次组件里state的改变，React都会通过调用它的render()方法重新渲染页面。
有两种方式使用`setState()`:
```js
**[terminal]
class Email extends React.Component {
  state = {
    subject: '',
    message: ''
  }
  // ...
});
```
这个例子中，组件的state包含了两个属性(`subject`和`message`)，它们也可以独自更新，比如:
```js
**[terminal]
this.setState({
  subject: 'Hello! This is a new subject'
})
```
通过这种方式，我们可以使`this.state.message`保持原样，但是可以用一个新值来替换`this.state.subject`。
第二种方式，我们可以通过给`setState()`传递一个函数，而并非传递一个对象。例如:
```js
**[terminal]
this.setState((prevState) => ({
  count: prevState.count + 1
}))
```
这里我们给函数传递了一个`prevState`参数。当一个组件的新的state依赖于之前的state时候(这里我们在之前的state的基础上加了1)，我们就可以用函数`setState()`

>###练习题
{% exercise %}
Define `x` equal to 10.

{% initial %}
var x =

{% solution %}
var x = 10;

{% validation %}
assert(x === 10);

{% context %}
// This is context code available everywhere
// The user will be able to evaluate `exposedVar`
var exposedVar = 3;
// ... or call `exposedFunction`
function exposedFunction {
    return 3;
}
{% endexercise %}


#小结
组件可以在初始化的时候设置state，这个state一般会根据用户的输入做出改变。组件可以使用`this.setState()`改变自己的内部state。每次state改变，React都会知道并且调用`render()`来重新渲染这个组件。这就给应用的UI提供了快速、有效的更新。

#延伸阅读:
- [Using State Correctly](https://facebook.github.io/react/docs/state-and-lifecycle.html) from React Docs

