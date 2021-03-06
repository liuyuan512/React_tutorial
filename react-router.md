{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-5ManagingAppLocation-1-1.mp4{% endvideo %}


#单页应用
单页应用可以以不同的方式运行。其中一种方式就是通过一次下载了所有的网页内容。通过这种方式，当你操作这个页面时，页面不需要刷新。另一种方式是通过加载用户请求的数据来渲染页面，这样当用户被导航到了新页面，就会有一步加载请求被执行。

在一个好的应用中，另一个关键因素就是URL控制着页面内容。单页应用是强交互的，用户只想能够通过URL来定位到指定的状态。当你把一个页面作为书签保存的时候，它只是一个URL。它并不记录这个页面的状态。

你应该注意到了我们之前做的应用不管你怎么操作交互，页面的URL都不会更新。

#React Router
React Router将React项目转变成单页应用。它通过提供一些特定的组件来实现这个目的。这些组件管理者links的创建，URL，提供不同URL位置的转换。

根据官方文档，React Router页面是这样写的:
>React Router是一系列导航组件的集合，这些组件与你的应用声明性的组合起来。

如果你感兴趣，可以点击这里 https://reacttraining.com/react-router/.

