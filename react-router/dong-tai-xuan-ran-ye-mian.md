这一部分，我们会先通过设定`this.state`的不同的值来动态性的渲染内容。 通过这个例子，我们可以弄清楚React Router是如何通过控制state来展示显示的内容的。接着会换成使用React Router来实现。

这里我需要做一个新的功能，就是添加一个联系人的功能。 但是我不想一次都把现有的联系人和需要添加联系人的表单都显示出来.这里我们会先通过控制state来控制页面的显示。

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/5ySqH5Uag2M.mp4{% endvideo %}
[视频里代码修改的地方](https://github.com/udacity/reactnd-contacts-complete/commit/db0aafdc7766048c28597d37f31977ac7833a62e)

在这个视频里我们创建了一个CreateContact组件，它将控制创建新的联系人。

这里做了一个简单的展示React Router的工作原理的事情，我们在`this.state`里添加了`screen`属性，并且用这个属性控制屏幕上应该显示的内容。如果`this.state.screen`是`list`，那么我们就显示已经存在的联系人。如果`this.state.screen`是`create`，那么我们将显示CreateContact组件

#添加按钮

现在我们不得不手动改变state来显示不同的内容。但是我们想要用户自己能够控制这个app,所以需要添加一个按钮

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/aOfohwGbL-A.mp4{% endvideo %}
[这里是视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/23a6a4dde977d7c18a3054a7b0b65f4fb4aad2ea)

#小结
在这部分添加的代码中，我们尝试了通过使用state来控制显示的内容。
下面我们换成用React Router来管理我们应用显示屏幕。
