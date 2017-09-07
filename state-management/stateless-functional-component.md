#函数性组件

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-3-1.mp4{% endvideo %}

对ES6不太熟悉的同学，可以点击这里[ES6 - JavaScript Improved](https://cn.udacity.com/course/es6-javascript-improved--ud356)，Udacity的免费课程。


下面我们看看什么是Stateless Functional Components

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-3-2.mp4{% endvideo %}
[视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/e763785368c5d99281182f5d11e03b5ba02541e0)

>###练习1
 什么时候适合使用Stateless Functional Components?
 - 当组件需要初始化一些数据的时候
 - 当组件只需要`render`方法的时候
 - 当组件不需要传入props的时候
 - 当组件不使用JSX的时候
 
 
>###练习2
 如果下面的`<IngredientList />`组件是一个Stateless Functional Components，那么在组件外部应该如何访问prop`items`?
 
>`<IngredientList items={ingredient.items} />`
 
 
#小结
如果你的组件不需要追踪内部状态(也就是说这个组件只需要一个`render()`方法)，你就可以把它声明为一个Stateless Functional Component。

下面的两种表达式方式是等价的

```js
class Email extends React.Component {
  render() {
    return (
      <div>
        {this.props.text}
      </div>
    );
  }
};
```

```js
const Email = (props) => (
  <div>
    {props.text}
  </div>
);
```
注意后面这个例子中，我们可以直接将`props`作为一个参数传递给组件，在组件内部直接访问`props`，不需要用`this.props`。

#延伸阅读
- [关于容器组件](http://charlee.li/react-container-components.html)
- [Creating Stateless Function Components](https://www.reactenlightenment.com/react-state/8.4.html) from the React Enlightenment book
- [Functional Components vs. Stateless Functional Components vs. Stateless Components](https://tylermcginnis.com/functional-components-vs-stateless-functional-components-vs-stateless-components/) from Tyler