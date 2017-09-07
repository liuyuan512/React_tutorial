#安装

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-2renderingui-3-1.mp4{% endvideo%}

JSX是非常棒的，但是在到达浏览器之前，它确实需要被转换为常规的JavaScript。我们通常使用像Bable这样的编译工具来为我们完成这个任务。通过构建工具（如Webpack）来运行Babel，该工具有助于将我们所有的资源（JavaScript文件，CSS，图像等）捆绑到Web项目中。

为了简化这些初始配置，我们可以使用Facebook的Create React App包来管理我们所有的设置！该工具非常有助于开始构建一个React应用程序，因为它可以配置零配置所需的一切！安装创建React应用程序（通过npm的命令行）。

```
npm install -g create-react-app
```

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-2renderingui-3-2.mp4{% endvideo%}

>#The Yarn Package Manager
下面这个视频是使用yarn start开启的服务。Yarn是一个类似于NPM的包管理工具。Yarn是由Facebook创造的，旨在改善一些缓慢或缺乏NPM的关键方面。
但是也不必非要安装yarn,视频里的每一次使用yarn都可以用npm换掉。


{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-2renderingui-3-3.mp4{% endvideo%}


#小结

Facebook的创建`create-react-app`是支持React应用程序的命令行工具。使用它，不需要安装或配置Webpack或像Babel这样的编译器。这些步骤全都由`create-react-app`帮我们做好了
下面的链接提供了更多关于`create-react-app`的信息
- [create-react-app](https://github.com/facebookincubator/create-react-app)on GitHub
- [create-react-app Release Post](https://facebook.github.io/react/blog/2016/07/22/create-apps-with-no-configuration.html)from the React blog
- [Updates to create-react-app](https://facebook.github.io/react/blog/2017/05/18/whats-new-in-create-react-app.html)from the React blog