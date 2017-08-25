#React是什么？

React是一个JavaScript工具，可以轻松推理，构建和维护无状态和有状态的用户界面。它提供了使用称为React节点的类似HTML的节点来将UI声明性地定义和划分为UI组件（React组件）的方法。React节点最终被转换成用于UI呈现的格式（例如，HTML / DOM，画布，svg等）。
这一部分首先将概括性的讲一下什么是React，以及React一般情况下的用法。先不要关注这一部分的React实现细节，通过这一节大概对React有个认知。后面几部分将会再详细讲述实现细节。

##使用React创建一个类似`<select>`的UI组件
这里是这个组件
<script async src="//jsfiddle.net/codylindley/s2pxp36L/embed/html,result/"></script>

当浏览器解析上面的元素树时，它将产生一个包含可以选择的项目的文本列表的UI。点击上面的JSFiddle中的“结果”选项卡，看看浏览器产生了什么。
浏览器，[DOM](http://domenlightenment.com/)和[shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Shadow_DOM)在幕后合作，将`<select>` HTML转换为UI组件。注意，`<select>`组件允许用户进行选择，从而存储该选择的状态（即，点击“Volvo”，那么选中的就是“Volvo”)。
可以通过使用React节点创建一个自定义的`<select>`来创建一个React组件，最终将被编译成HTML DOM中的HTML元素。

下面就使用React创建一个`<select>`样UI组件。

##定义一个UI组件
下面将通过引用`React.createClass`函数来创建一个`MySelect`React组件。
这个将要创建的`MySelect`组件将由一些样式和一个空的React`<div>`节点元素构成。
```js
**[terminal]

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
**[terminal]

return React.createElement('div', { style: mySelectStyle });
```
而不是这样:
```js
**[terminal]

return <div style={mySelectStyle}></div>;
```
现在，请记住，当在React代码中编写类似HTML的标签时，最终必须将其转换为真正的JavaScript以及任何ES6语法。
现在，`<MySelect>`组件由一个空的React `<div>`节点元素组成。现在它没有任何功能，下面坐做出一点修改。
这里再定义另一个名为`<MyOption>`的组件，然将在`<MySelect>`组件中使用`<MyOption>`组件。

看一下下面更新的JavaScript代码，定义了`<MySelect>`和`<MyOption>` React组件。

```js
**[terminal]

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


##通过使用React的props向组件传递属性


请注意，`<MyOption>`组件由一个包含表达式`{this.props.value}`的`<div>`组成。对于JSX，{}括号表示正在使用JavaScript表达式。换句话说，用{}你可以写JavaScript代码。

{}括号用于访问（即`this.props.value`）到由`<MyOption>`组件传递的属性或属性。换句话说，当`<MyOption>`组件被渲染时，使用类似HTML的属性（即value =“Volvo”）传递的值选项将被放置到`<div>`中。这些HTML查看的属性被认为是React属性/道具。 React使用它们将无状态/不可变选项传递到组件中。在这种情况下，我们只是将值prop传递给`<MyOption>`组件。与参数传递给JavaScript函数的方式差不多。

##将组件渲染到Virtual DOM，然后是HTML DOM


此时我们的JavaScript只定义了两个React Components。我们还没有将这些组件实际呈现给虚拟DOM，从而实现到HTML DOM。
在我们这样做之前，说一下到目前为止，我们所做的是使用JavaScript定义两个React组件。在理论上，我们迄今为止的JavaScript只是UI组件的定义。它不是严格地要进入一个DOM，甚至一个虚拟DOM。在理论上，同样的定义也可以用于将此组件呈现到[native mobile platform ](https://github.com/facebook/react-native)或[HTML Canvas](https://github.com/Flipboard/react-canvas)。但我们不会这样做。这里只要知道React是一个可以超越DOM，前端应用程序甚至[Web平台](https://facebook.github.io/react/docs/react-api.html)的UI的模式。

现在让我们将`<MySelect>`组件呈现给虚拟DOM，而后者又会将其转换为HTML页面内的实际DOM。
在下面的JavaScript中，我在最后一行添加了一个对`ReactDOM.render（）`函数的调用。在这里，我将`ReactDOM.render（）`函数传递给我们要呈现的组件（即`<MySelect>`），并引用HTML DOM中的HTML元素（即`<div id =“app”> </ div >`）,即我想渲染我的React` <MySelect>`组件的地方。
下面单击“Result”选项卡，将看到我们自定义的React `<MySelect>`组件呈现给HTML DOM。
<script async src="//jsfiddle.net/codylindley/zp86ez31/embed/js,html,result/"></script>


请注意，我所做的只是告诉React从哪里开始渲染组件和从哪个组件开始渲染。然后React会渲染包含在起始组件（即`<MySelect>`）中的任何子组件（即`<MyOption>`）。
你可能在想，我们根本没有创建一个`<select>`。我们所做的只是创建一个静态/无状态的文本字符串列表。接下来我们会解决。
在我开始之前，我想指出，没有写入隐式DOM交互来将`<MySelect>`组件导入到真正的DOM中。换句话说，在创建此组件期间没有调用jQuery代码。与实际的DOM的交互都被React的虚拟DOM所抽象。实际上，当使用React时，你正在做的是描述React所用的虚拟DOM，并为其创建一个真正的DOM。

##使用React的state

为了使我们的`<MySelect>`组件模仿一个本地的`<select>`元素，我们将向组件添加状态。毕竟，如果不能保持选择的状态，那么自定义`<select>`元素是没有意义的。
当组件包含信息快照时，state通常避免不了。我们的定制`<MyOption>`组件，它的状态是当前选择的文本或没有选择任何文本。请注意，state通常涉及用户事件（即鼠标，键盘，剪贴板等）或网络事件（即AJAX），并且其值用于确定UI何时需要重新呈现（即，当值更改时重新渲染）。
状态通常位于组成UI组件的最顶层组件上。使用React getInitialState（）函数，我们可以通过在调用getInitialState时返回一个状态对象（即return {selected：false};）），将组件的默认状态设置为false（即没有选择）。 getInitialState生命周期方法在组件装入之前被调用一次。返回值将用作this.state的初始值。
我已经更新了下面的代码，以将状态添加到组件。当我更新代码时，请确保阅读JavaScript注释，注意代码中的更改。
```js
**[terminal]

var MySelect = React.createClass({
    getInitialState: function(){ //add selected, default state
        return {selected: false}; //this.state.selected = false;
    },
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return (
            <div style={mySelectStyle}>
                <MyOption value="Volvo"></MyOption>
                <MyOption value="Saab"></MyOption>
                <MyOption value="Mercedes"></MyOption>
                <MyOption value="Audi"></MyOption>
            </div>
        );
    }
});

var MyOption = React.createClass({
    render: function(){
        return <div>{this.props.value}</div>;
    }
});

ReactDOM.render(<MySelect />, document.getElementById('app'));
```


使用默认状态设置，接下来我们将添加一个名为select的回调函数，当用户单击某个选项时，该函数将被调用。在这个函数的内部，我们得到所选择的选项的文本（通过事件参数），并使用它来确定当前组件的setState。请注意，我正在使用传递给选择回调的事件详细信息。如果你有任何jQuery的经验，这种模式应该很熟悉。
```js
**[terminal]

var MySelect = React.createClass({
    getInitialState: function(){
        return {selected: false};
    },
    select:function(event){// added select function
        if(event.target.textContent === this.state.selected){//remove selection
            this.setState({selected: false}); //update state
        }else{//add selection
            this.setState({selected: event.target.textContent}); //update state
        }   
    },
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return (
            <div style={mySelectStyle}>
                <MyOption value="Volvo"></MyOption>
                <MyOption value="Saab"></MyOption>
                <MyOption value="Mercedes"></MyOption>
                <MyOption value="Audi"></MyOption>
            </div>
        );
    }
});

var MyOption = React.createClass({
    render: function(){
        return <div>{this.props.value}</div>;
    }
});

ReactDOM.render(<MySelect />, document.getElementById('app'));
```


为了让我们的<MyOption>组件能够访问select函数，我们必须通过`props`从`<MySelect>`组件向`<MyOption>`组件传递对它的引用。为此，我们将`select = {this.select}`添加到`<MyOption>`组件。
有了这一点，我们可以将`onClick = {this.props.select}`添加到`<MyOption>`组件。希望很明显，我们所做的一切都是可以链接一个可以调用select函数的点击事件。 React负责为实际链接真正的DOM中的点击处理程序。

```js
**[terminal]

var MySelect = React.createClass({
    getInitialState: function(){
        return {selected: false};
    },
    select:function(event){
        if(event.target.textContent === this.state.selected){
            this.setState({selected: false});
        }else{
            this.setState({selected: event.target.textContent});
        }   
    },
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return (//pass reference, using props, to select callback to <MyOption>
            <div style={mySelectStyle}>
                <MyOption select={this.select} value="Volvo"></MyOption>
                <MyOption select={this.select} value="Saab"></MyOption>
                <MyOption select={this.select} value="Mercedes"></MyOption>
                <MyOption select={this.select} value="Audi"></MyOption>
            </div>
        );
    }
});

var MyOption = React.createClass({
    render: function(){//add event handler that will invoke select callback
        return <div onClick={this.props.select}>{this.props.value}</div>;
    }
});

ReactDOM.render(<MySelect />, document.getElementById('app'));
```


通过这样做，我们现在可以通过点击其中一个选项来设置状态。换句话说，当单击选项时，选择功能将运行并设置MySelect组件的状态。然而，组件的用户不知道这是做的，因为我们所做的是更新我们的代码，以便状态由组件管理。在这一点上，我们在视觉上没有任何反馈。我们来解决这个问题。
接下来我们需要做的是将当前状态转移到`<MyOption>`组件，以便它能够可视地响应组件的状态。
再次使用道具，我们将通过将所有`<MyOption>`组件中的属性`state = {this.state.selected}`从`<MySelect>`组件向下传递到`<MyOption>`组件。现在我们知道该选项的状态（即`this.props.state`）和当前值（即`this.props.value`），我们可以验证该状态是否与给定的`<MyOption>`组件中的值相匹配。如果是这样，我们就知道应该选择这个选项。我们通过编写一个简单的if语句，如果状态与当前选项的值相匹配，则将简写的if语句添加到JSX `<div>`中添加样式选择状态（即`selectedStyle`）。否则，我们返回一个具有`unSelectedStyle`样式的React元素。

<script async src="//jsfiddle.net/codylindley/L1z9za23/embed/js,html,result/"></script>


确保您点击上面的“Result”标签，并使用自定义的“React select”组件来验证新功能。
虽然我们的React UI选择组件不像你所希望的那样漂亮或功能完整，但我希望你可以理解它工作的方式。 React是一种可以帮助你在结构树（即组件树）中推理，构造和维护无状态和有状态UI组件的工具。
在转向虚拟DOM的角色之前，我想强调，您不必使用JSX和Babel。您可以随时绕过这些工具，并直接写入JavaScript。下面，我在JSB被Babel转换后，显示代码的最终状态。如果您选择不使用JSX，那么你必须自己编写以下代码，而不是我在本节中编写的代码。

```js
**[terminal]

var MySelect = React.createClass({
  displayName: 'MySelect',

  getInitialState: function getInitialState() {
    return { selected: false };
  },
  select: function select(event) {
    if (event.target.textContent === this.state.selected) {
      this.setState({ selected: false });
    } else {
      this.setState({ selected: event.target.textContent });
    }
  },
  render: function render() {
    var mySelectStyle = {
      border: '1px solid #999',
      display: 'inline-block',
      padding: '5px'
    };
    return React.createElement(
      'div',
      { style: mySelectStyle },
      React.createElement(MyOption, { state: this.state.selected, select: this.select, value: 'Volvo' }),
      React.createElement(MyOption, { state: this.state.selected, select: this.select, value: 'Saab' }),
      React.createElement(MyOption, { state: this.state.selected, select: this.select, value: 'Mercedes' }),
      React.createElement(MyOption, { state: this.state.selected, select: this.select, value: 'Audi' })
    );
  }
});

var MyOption = React.createClass({
  displayName: 'MyOption',

  render: function render() {
    var selectedStyle = { backgroundColor: 'red', color: '#fff', cursor: 'pointer' };
    var unSelectedStyle = { cursor: 'pointer' };
    if (this.props.value === this.props.state) {
      return React.createElement(
        'div',
        { style: selectedStyle, onClick: this.props.select },
        this.props.value
      );
    } else {
      return React.createElement(
        'div',
        { style: unSelectedStyle, onClick: this.props.select },
        this.props.value
      );
    }
  }
});

ReactDOM.render(React.createElement(MySelect, null), document.getElementById('app'));
```

##理解虚拟DOM的作用
在这里再讨论一下React虚拟DOM的优点来完成这个React概述。
希望你注意到，在创建我们的自定义选择UI时，我们唯一与真实DOM进行交互的是当我们告诉ReactDOM.render（）函数在HTML页面中渲染我们的UI组件（即，将其渲染为`<div id = "app"> </div>`）。这可能只是在从React组件树构建React应用程序时，与真正的DOM唯一的交互。在这里，它的价值在于React。通过使用React，你真的不必像你曾经在编写jQuery代码一样考虑DOM。通过从代码中删除大部分（如果不是全部）隐含的DOM交互，React将作为一个完整的DOM抽象来替代jQuery。当然，这不是唯一的优点。
因为DOM已被虚拟DOM完全抽象，所以允许在状态改变时更新真正的DOM的繁重的性能模式。虚拟DOM根据状态和道具来跟踪UI变化。然后将其与真实的DOM进行比较，然后仅进行更新UI所需的最小更改。换句话说，真正的DOM只有当state或props改变时才需要的最小化的变化。
实时查看这些性能更新通常会澄清有关执行者DOM差异的任何混淆。看下面的动画图片，展示我们在本章中创建的UI组件的用法（即改变状态）。
请注意，随着UI组件更改状态，只有最终需要的对实际DOM的更改正在发生。我们知道React正在做这件事，因为实际上正在更新的真正的DOM的唯一部分是具有绿色轮廓/背景的部分。整个UI组件在每个状态更改时只是更新需要更改的部分，其他的地方都没有被更新，

让我们弄清楚一点，这不是一个革命性的概念。你可以用一些精心制作和表现出色的jQuery代码来完成同样的事情。但是，通过使用React，你很少会考虑它。虚拟DOM正在为你做所有的性能工作。从某种意义上说，这是最好的jQuery / DOM抽象类型。一个你甚至不必担心或代码的DOM。这一切都发生在幕后，没有你隐含地必须与DOM本身进行交互。
当与隐式jQuery代码相比，虚拟DOM当然是一种缓解，而React的价值并不在虚拟DOM上。虚拟DOM只是蛋糕上的糖衣。简单地说，React的价值取决于它为创建一个UI组件树提供了一个简单和可维护的模式。想象一下，通过使用可重复使用的React组件来定义应用程序的整个界面，可以简化UI的编程。