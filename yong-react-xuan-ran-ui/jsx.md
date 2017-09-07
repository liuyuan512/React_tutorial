#嵌套元素
我们看一下如果元素需要嵌套应该怎么做

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-2renderingui-2-2.mp4{% endvideo %}
{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-2renderingui-2-3.mp4{% endvideo %}

#`.createElement()`只能返回一个根元素
因为`React.createElement( /* type */, /* props */, /* content */ )`只能创建一种特定的React元素，通常就传递一个`<div>`或者`<span>`标签来表示React元素的类型，这里的`content`属性其实可以是任何内容，也就是说可以再嵌套一个React元素
```js
const element = React.createElement('div', null,
  React.createElement('strong', null, 'Hello world!')
);
```
当这个React元素作为HTML被渲染时，'Hello world'被嵌套在了一个<div>标签里。也就是说我们可以深层嵌套，但是注意最后的调用一定只能是返回一个单个元素

###JSX的由来

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-2renderingui-2-4.mp4{% endvideo %}


###下面我们把`React.createElement()`替换成JSX
{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-2renderingui-2-5.mp4{% endvideo %}

#练习
>给一个JSX：
```js
const greeting = (
  <div className='greeting'>
    <h2>Hello world!</h2>
  </div>
);
```

>如果我们想要输出同样的HTML，那么空白处需要依次填写什么内容?
```js
const greeting = React.createElement(
  __1__,
  { className: 'greeting' },
  React.createElement(
    __2__,
    {},
    __3__
  )
);
```

#JSX也返回一个唯一的根元素
当用JSX的时候，要牢记它最后返回的必须是一个元素。这个元素可以有很多子元素，但是必须都得包裹在一个根元素里(比如<div>和<span>)，看这个例子
```js
const message = (
  <div>
    <h1>All About JSX:</h1>
    <ul>
      <li>JSX</li>
      <li>is</li>
      <li>awesome!</li>
    </ul>
  </div>
);
```

这个例子就展示了最后返回的是一个`<div>`但是有很多子元素嵌套在里面。下面的这个写法就会引发一个错误
```js
const message = (
  <h1>All About JSX:</h1>
  <ul>
    <li>JSX</li>
    <li>is</li>
    <li>awesome!</li>
  </ul>
);
```
这个例子中，我们有两个兄弟元素在根位置(`<h1>`和`<ul>`)。这将会引发一个错误
>Syntax error: Adjacent JSX elements must be wrapped in an enclosing tag

JSX只是对`.createElement()`的语法扩展，由于`.createElement()`只能将一个标签名(字符串类型的)作为第一个参数，所以JSX也只能返回一个根元素。

#JSX用于组件
我们将JSX用在React的组件中来渲染UI。组件是指可以重复使用的代码段，并且对最终渲染到页面上的内容负责。
由于React的主要作用就是创建我们应用的UI，所以在组件类里唯一要求实现的就是`render()`函数

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-2renderingui-2-6.mp4{% endvideo %}
#在React中声明组件
在上个视频中，我们这样定义`ContactList`
```js
class ContactList extends React.Component {
// ...
}
```
也就是说，我们定义了组件，这个组件是一个继承自`React.Component`的JavaScript类。

在实际工程里，会经常这样声明一个组件
```js
class ContactList extends Component {
// ...
}
```
这就需要从React导入:
```js
import React, { Component } from 'react';
```

#小结
React只关注于应用的View层。我们可以用`.createElement()`来渲染HTML。但是实际中会经常用JSX来描述UI，JSX只是一个语法扩展。，写起来很像HTML。JSX在编译的时候会被编译成React的`.createElement() `方法来输出需要浏览器渲染的HTML。

在创建React应用的时候应该用组件。组件代表了React的复用性和模块性。可以把`component`类当做可以实例化组件的工厂。这个`component`类需要遵守"DOT"(do one thing)原则。如果一个组件需要处理很多任务，那么最好把它拆分成更多小的组件。

##延伸阅读:
- [Rendering Elements](https://facebook.github.io/react/docs/rendering-elements.html) from the React docs
- [jsx介绍](http://www.infoq.com/cn/articles/react-jsx-and-component) from InfoQ


