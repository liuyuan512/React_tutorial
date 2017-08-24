#Hello world
在React里面，我们用`.createElement()`方法来创建元素
```
React.createElement( /* type */, /* props */, /* content */ );
```
看一下每个参数的作用:
- `type`-可以是一个字符串或者React元素
   这里可是是一个任意HTML元素的字符串(比如'p','span','header')或者你可以传递一个React组件
- `props`-可以是`null`或者一个对象
   这是一个HTML属性和用户数据的对象
- `content`-`null`,一个字符串，React元素或者React组件
传递到这里的内容将会被渲染。包括纯text文本，JavaScript代码或者其它的React元素等

下面创建一个Hello World元素


```
const element = React.creactElement('div',null,'hello world')
```

元素创建完毕以后，我们需要把这个元素渲染到浏览器

```
ReactDOM.render(element,document.getElementById('root'))
```
此时hello world 就已经被我们渲染出来了

![](/assets/Screen Shot 2017-08-23 at 16.27.12.png)

那么我们渲染的这个元素到底是什么呢？我们在console里来看一下
```
console.log(element)
```
![](/assets/Screen Shot 2017-08-23 at 15.45.04.png)
对，就是一个JavaScript的对象。

这个对象的type属性，就是我们创建的元素里面的第一个参数的值。

{% video controls="controls" %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/MTXIx7859P0.mp4{% endvideo %}

我们把React元素渲染到了一个叫做`root`的DOM节点，那么这个`root`来自哪里呢？
由React创建的应用会有一个唯一的`root`DOM节点。HTML文件会包含一个如下的`<div>`
```
<div id='root'></div>
```
通过把这个DOM节点传递到这个`getElementById()`里面，React会最终控制其内容。

还可以这样想，这个特定的`<div>`将作为我们的React应用程序的‘钩子’，在这里React会接管并且渲染UI。

#props
下面我们给我们创建的元素的第二个参数传递一个值
```
const element = React.creactElement('div',{
 className:'welcome-message'
},'hello world')

```
注意这里传递的是'className'，这时可以在开发者工具上的Elements上看到我们的`<div>`元素

![](/assets/Screen Shot 2017-08-23 at 16.25.13.png)

你会看到`<div>`的class属性是`welcome-message`。 这是因为我们创建元素的时候，描述的是DOM节点，并不是HTML元素。 Class是HTML元素的属性名称，一旦浏览器解析React元素，就会把它转变成真正的DOM节点里的DOM属性名，即class。
所以我们要切记我们在创建React元素的时候，我们描述的是DOM节点，而不是HTML字符串。

需要时刻牢记的是，当我们用React.creactElement的时候，我们并没有创建实际的DOM节点。直到render之后，浏览器才会创建真实的DOM节点。

#测试
下列代码运行时，`myBio`的值是什么属性？
```
import React from 'react';

const myBio = React.createElement(
    'div',
    null,
    'My name is Michael, and I love porcupines.'
);
```
>- 一个指向DOM节点的指针
 - 一个DOM节点
 - 一个JavaScript对象
 - 一个JavaScript类
 
   