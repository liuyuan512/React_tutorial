#Route组件

我们最后需要的组件就是`Route`
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/NlHLfRb6T_E.mp4{% endvideo %}

最后我们需要做的这一步就是让React Router来管理URL和UI
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/KsuuFWh1VAg.mp4{% endvideo %}
[这里是视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/0c1056088f055e7f1046531142f56201d3f18cd6)

#小结
你可以向<Route>传递一个router要渲染的组件作为props,需要使用`Route`的`render` prop.然后`render`会让你掌控想要渲染的组件，你可以向这个组件里传递任何你向传递的props。

总之Route组件是用React Router构建应用的很关键的组件，因为是这个组件决定了根据当前的URL路径要渲染的内容。