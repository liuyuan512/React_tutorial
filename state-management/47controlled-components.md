#Controlled Components
通常我们在一个网页应用里使用表单的时候，表单的状态都会存储在DOM里面。但React追求的帮我们我们更有效的管理应用内的state。那么React内是如何使用表单的呢？

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-7-1.mp4{% endvideo %}

#React开发工具
`React Developer Tools`可以让你在开发的时候检查组件内部的state和props。安装[Chrome插件](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en-US),打开Chrome console牛可以看到`React`选项卡。有关细节，可以参考[官方文档](https://github.com/facebook/react-devtools)
下面看一下如何创建一个Controlled Component

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-7-2.mp4{% endvideo %}
[视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/ce3a9a8a0f1d8d0224eba663e512cd309fb1f804)

注意`<input>`的`value`属性。显示的value已经和组件的state的value绑定了，这样一来，`state`就成了唯一数据源。
因为是React最终控制着input表单元素的value，我们就成这个组件为[Controlled Component](https://facebook.github.io/react/docs/forms.html#controlled-components)

总结一下用户的输入是如何影响组件`ListContacts`自己的state的:
 1. 用户向input区域输入文本
 2. 在每一个onChnage事件上都设置一个事件监听器，它会触发`updateQuery()`函数
 3. 函数`updateQuery()`会调用`setState()`,将新的state融入组件的内部state
 4. 由于组件的state发生了改变，组件`ListContacts`重新渲染
 
下面看一下，如何利用这个更新的`state`来过滤我么的contacts。先安装一下下面两个包，以帮我们过滤
- [escape-string-regexp](https://www.npmjs.com/package/escape-string-regexp)
- [sort-by](https://www.npmjs.com/package/sort-by)

```
**[terminal]

npm install --save escape-string-regexp sort-by
```

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-7-3.mp4{% endvideo %}
[视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/abd5fccf9a69546e75d9c178379d3ef92405719e)

到这里，我们的组件显得有点笨拙。render()方法经常访问state对象的`query`属性(`this.state.query`)，也经常访问props对象的`contacts`属性(`this.props.contacts`)。因为`props`和`state`都只是JavaScript对象，我们可以利用ES6的特性来重构一下，这样就质疑直接使用这个变量，而不用每一次都通过`this.state.query`和`this.props.contacts`访问了。这个过程叫做[解构赋值](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

这样做并不会改变我们代码的返回值，但是可以使我们的代码开起来更整洁一点。看一下具体怎么做

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-7-4.mp4{% endvideo %}
[这里是视频中代码修改的部分](https://github.com/udacity/reactnd-contacts-complete/commit/4f7055abb1c197c1c5c968b472a643dedcb90ba1)

#显示联系人计数
马上就要完成这个controlled component了。最后一步是在我们的应用里显示有多少联系人显示了出来，总数一共是多少
{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-7-5.mp4{% endvideo %}
[这里是视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/1ca08610c76a33da761b6d85e303cd8c436519de)

#小结
Controlled components是指可以渲染表单的组件，但是表单的数据源是存储于组件内部的，而不是在DOM里面。Controlled Component的益处有:
- 及时的输入验证
- 有条件的启用/禁用按钮
- 强制输入格式

在`ListContacts`组件里，这个组件不仅仅可以渲染出一个表单，并且还可以根据用户的输入控制事件发生。在这个例子里面，event handlers会根据用户的输入更新组件的state。并且我们也知道了只要React的state发生改变，都会引起React的重新渲染，高效率的实时显示我们的搜索结果。