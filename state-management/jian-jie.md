#简介
现在看一下React中非常重要的三个概念
- Props------允许向组件内传递数据
- Functional Components(函数式组件)---------创建React组件最直接的方式
- Controlled Components(控制组件)----------绑定表单和组件状态

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-1-1.mp4{% endvideo %}

下面我们通过一起来做一个小应用，来理解和熟悉React中的各种概念，先看一下这个应用的各种功能

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/Ju5mbCEFe9Q.mp4{% endvideo %}

#移除默认文件
`Create React App`会自动产生一些默认文件。这里提供两种方式来删除默认的文件，并且添加上这里提供给你的文件。你可以选择自己一步步手动添加，也可以克隆这个[this repo](https://github.com/udacity/reactnd-contacts-complete)并且记得chekout这个`starter-files-added`分支，这样你就不用手动操作了。

如果你打算自己手动删除默认文件并且添加我们提供的内容，就就继往下看。如果你决定克隆这个已经修改好的文件，那么就直接跳转到底部设置后端服务器。

如果你想自己手动执行这些改变，第一步就是删除这些`Create React App`产生的样板文件，你可以点击这里查看修改细节[this commit](https://github.com/udacity/reactnd-contacts-complete/commit/b1959521da8d914374bd2a61b17e55088ffab9f5)

#添加提供的文件
这个教程专注于用React构建应用。为了使样式不太丑，这里提供了样式文件。
点击[this commit](https://github.com/udacity/reactnd-contacts-complete/commit/6f38f078634d104a62e3024cab4cc2d592dd82f6)查看修改细节，添加到自己的文件中。如果你是选择克隆的，记得要`npm install`
以确保所有的依赖都被安装好。

#后端服务器
我们构建的Contacts应用是一个前端应用，但是我们最终的数据是存储在后端服务器里的。这里提供好了保存数据的后端服务器。
你需要做的是:
- clone这个项目`git clone https://github.com/udacity/reactnd-contacts-server.git`
- 安装项目依赖 `npm install`
- 开启服务器 `node server.js`

一旦开启了服务器，你就可以把它放到一边。Contacts项目会与这个服务器交互，但不会修改它的数据。

#注意
这里你是运行了两个服务器
- 前端:在端口**port 3000**(with `npm start` or `yarn start`)
- 后端: 在端口**port 5001 **(with `node server.js`)
确保两个服务器都在运行