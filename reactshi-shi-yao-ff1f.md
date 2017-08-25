#React是什么？

React是一个JavaScript工具，可以轻松推理，构建和维护无状态和有状态的用户界面。它提供了使用称为React节点的类似HTML的节点来将UI声明性地定义和划分为UI组件（React组件）的方法。React节点最终被转换成用于UI呈现的格式（例如，HTML / DOM，画布，svg等）。
这一部分首先将概括性的讲一下什么是React，以及React一般情况下的用法。先不要关注这一部分的React实现细节，通过这一节大概对React有个认知。后面几部分将会再详细讲述实现细节。

##使用React创建一个类似`<select>`的UI组件


[source code](https://jsfiddle.net/codylindley/s2pxp36L/embed/html,result/)
<script async src="//jsfiddle.net/codylindley/s2pxp36L/embed/html,result/"></script>
当浏览器解析上面的元素树时，它将产生一个包含可以选择的项目的文本列表的UI。点击上面的JSFiddle中的“结果”选项卡，看看浏览器产生了什么。
浏览器，[DOM](http://domenlightenment.com/)和[shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Shadow_DOM)在幕后合作，将`<select>` HTML转换为UI组件。注意，`<select>`组件允许用户进行选择，从而存储该选择的状态（即，点击“Volvo”，那么选中的就是“Volvo”)。
可以通过使用React节点创建一个自定义的`<select>`来创建一个React组件，最终将被编译成HTML DOM中的HTML元素。

下面就使用React创建一个`<select>`样UI组件。

##定义一个UI组件
下面将通过引用`React.createClass`函数来创建一个`MySelect`React组件。
这个将要创建的`MySelect`组件将由一些样式和一个空的React`<div>`节点元素构成。
```js
var MySelect = React.createClass({ //define MySelect component
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        // using {} to reference a JS variable inside of JSX
        return <div style={mySelectStyle}></div>; //react div element, via JSX
    }
});
```


那个`<div>`是一个类似HTML的标签，在JavaScript中称为JSX。 JSX是一种React使用的可供选择的自定义的JavaScript语法，它可以可映射到真实HTML元素，自定义元素和文本节点。使用JSX定义的React节点不是与HTML元素一对一的匹配。这里有一些[不同](https://facebook.github.io/react/docs/dom-elements.html)和[陷阱](https://facebook.github.io/react/docs/jsx-in-depth.html)

JSX语法必须从JSX转换为真实的JavaScript，以便由ES5的JS引擎解析。上面的代码，如果没有转换，当然会导致JavaScript错误。
用于将JSX转换为实际JavaScript代码的官方工具称为Babel。
在Babel（或类似的东西）之后，将上述代码中的JSX <div>转换成真正的JavaScript，它将如下所示

```js
return React.createElement('div', { style: mySelectStyle });
```
而不是这样:
```js
return <div style={mySelectStyle}></div>;
```
现在，请记住，当在React代码中编写类似HTML的标签时，最终必须将其转换为真正的JavaScript以及任何ES6语法。
现在，`<MySelect>`组件由一个空的React `<div>`节点元素组成。现在它没有任何功能，下面坐做出一点修改。
这里再定义另一个名为`<MyOption>`的组件，然将在`<MySelect>`组件中使用`<MyOption>`组件。

看一下下面更新的JavaScript代码，定义了`<MySelect>`和`<MyOption>` React组件。

```js
var MySelect = React.createClass({
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return ( //react div element, via JSX, containing <MyOption> component
            <div style={mySelectStyle}>
                <MyOption value="Volvo"></MyOption>
                <MyOption value="Saab"></MyOption>
                <MyOption value="Mercedes"></MyOption>
                <MyOption value="Audi"></MyOption>
            </div>
        );
    }
});

var MyOption = React.createClass({  //define MyOption component
    render: function(){
        return <div>{this.props.value}</div>; //react div element, via JSX
    }
});
```
注意看一下`<MyOption>`组件是怎样用在`<MySelect>`内部的，使用了JSX语法。


##通过使用React的props想组件传递属性


请注意，`<MyOption>`组件由一个包含表达式`{this.props.value}`的`<div>`组成。对于JSX，{}括号表示正在使用JavaScript表达式。换句话说，用{}你可以写JavaScript代码。

{}括号用于访问（即`this.props.value`）到由`<MyOption>`组件传递的属性或属性。换句话说，当`<MyOption>`组件被渲染时，使用类似HTML的属性（即value =“Volvo”）传递的值选项将被放置到`<div>`中。这些HTML查看的属性被认为是React属性/道具。 React使用它们将无状态/不可变选项传递到组件中。在这种情况下，我们只是将值prop传递给`<MyOption>`组件。与参数传递给JavaScript函数的方式差不多。

##将组件渲染到Virtual DOM，然后是HTML DOM


此时我们的JavaScript只定义了两个React Components。我们还没有将这些组件实际呈现给虚拟DOM，从而实现到HTML DOM。
在我们这样做之前，说一下到目前为止，我们所做的是使用JavaScript定义两个React组件。在理论上，我们迄今为止的JavaScript只是UI组件的定义。它不是严格地要进入一个DOM，甚至一个虚拟DOM。在理论上，同样的定义也可以用于将此组件呈现到[native mobile platform ](https://github.com/facebook/react-native)或[HTML Canvas](https://github.com/Flipboard/react-canvas)。但我们不会这样做。这里只要知道React是一个可以超越DOM，前端应用程序甚至[Web平台](https://facebook.github.io/react/docs/react-api.html)的UI的模式。

现在让我们将`<MySelect>`组件呈现给虚拟DOM，而后者又会将其转换为HTML页面内的实际DOM。
在下面的JavaScript中，我在最后一行添加了一个对`ReactDOM.render（）`函数的调用。在这里，我将`ReactDOM.render（）`函数传递给我们要呈现的组件（即`<MySelect>`），并引用HTML DOM中的HTML元素（即`<div id =“app”> </ div >`）,即我想渲染我的React` <MySelect>`组件的地方。
下面单击“Result”选项卡，将看到我们自定义的React `<MySelect>`组件呈现给HTML DOM。
[source code](https://jsfiddle.net/codylindley/zp86ez31/embed/js,html,result/)
<script async src="//jsfiddle.net/codylindley/zp86ez31/embed/js,html,result/"></script>