#State
之前的`props`是指从父组件传递过来的属性，而且不能修改，是"只读属性"。

那么组件的`state`属性，就是指可以被修改的，而且会影响到最终页面渲染的内容。这一部分，我们看一下如何将state管理的复杂性封装到各个对的组件之中去的。

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/W-udVlRApio.mp4{% endvideo %}

>##注意!
 上面的代码里，我们直接将`state`对象放入了class里面，并没有通过`constructor()`方法
 ```js
   class User extends React.Component {
    state = {
      username: 'Tyler'
    } 
  }
  
>  // rather than
  
>  class User extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        username: 'Tyler'
      }
    }
  }
 ```
>这一点和Facebook的[Setting the Initial State docs](https://facebook.github.io/react/docs/react-without-es6.html#setting-the-initial-state) 不太一样。

>在`constructor()`之外直接设置`state`意味着它是一个类[class fields](https://github.com/tc39/proposal-class-fields)，一个语言的新特性。暂时还没有被JavaScript支持，但是多亏了强大的Babel的转译能力，我们可以使用它！

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/RyO7B5KLXVY.mp4{% endvideo %}
[这里是视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/c4b43702554a8bf732eef6264c7053c370c6b201)


>##注意！
 当定义一个组件的初始state时候，要避免用`props`赋值。因为这样做的话，state只会在刚创建的时候被`props`初始化一次。
 ```js
 this.state = {
  user: props.user
}
 ```
>这个例子里，如果`props`的值被更新，那么当前的state将不会跟着更新，只有在这个组件”被刷新“的时候才会更新。 用`props`赋值初始化state同样也会导致数据重复，违背了React的单一数据源原则。

>###练习
下面关于`state`说法正确的是哪些？
- 组件的state可以再初始化的时候定义
- state通常是有组件外部传递
- state应该存放永远不会改变的信息
- 组件可以修改自己内部的state


#小结
通过组件自己管理自己的state，state一旦发生改变，React就会知晓并且自动的对页面做出必要的更新。
使用React构建UI组件时的一个重要的好处就是:当更新页面的时候，我们只需要关注于更新state。 我们不需要关心每一的更新的时候页面的那一部分需要改变。我们不需要决定怎么做才能更有效率的渲染页面。React会对比当前的结果和之前的结果，替我们做出决定改变页面的哪一部分。

#延伸阅读
- [Identify Where Your State Should Live](https://facebook.github.io/react/docs/thinking-in-react.html#step-4-identify-where-your-state-should-live)