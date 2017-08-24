#组件
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/-AVOIP-L7oo.mp4{% endvideo %}
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/PtospOO4qrs.mp4{% endvideo %}
[视频中代码修改的地方](https://github.com/udacity/reactnd-contacts-complete/commit/069bbfa3f5359849d334a0f58813220291e61dc0)

#组件的概念
React使用组件来封装界面模块，整个界面就是一个大组件，开发过程就是不断优化和拆分界面组件、构造整个组件树的过程。可以认为组件类似于其他框架中Widget（或Control）的概念，但又有所不同。React中的界面一切皆为组件，而Widget一般只是嵌入到界面中为完成某个功能的独立模块。

如下图，整个页面是一个大的组件，然后再将其拆分成很多小的组件。组件机制加上JSX的语法，让你在构造界面时就像有一套符合项目需求的HTML标记，界面定义变得非常直观。
![](/assets/component.png)