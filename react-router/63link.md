#Link组件
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/qbP07LypkN8.mp4{% endvideo %}
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/V3kc4Sz1GII.mp4{% endvideo %}
[这里是视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/4fa3926892f6292fe562902ca1b1e3c9d840f27a)

`<Link>`是一个提供声明式的，易于导航的组件。通过传入一个`to`属性，你就可以告诉它导航到哪个路径。
```
<Link to="/about">About</Link>
```
有时候我们需要的链接要比字符串稍微复杂一点。例如，你可以传递一个查询参数或者链接到一个页面的指定位置。如果你想向新的路由传递状态呢？你可以向`<Link>`的`to`prop传递这个对象
```js
<Link to={{
  pathname: '/courses',
  search: '?sort=name',
  hash: '#the-hash',
  state: { fromDashboard: true }
}}>
  Courses
</Link>
```
你不需要总是使用这个特性，但是了解一下总是好的。关于`<Link>`更详细的信息，你可以点击[官方文档](https://reacttraining.com/react-router/web/api/Link)

#Link小结

React Router提供了一个`Link`组件，它可以让你添加声明式的，易于访问的导航在你的应用中。你可以用它来替代原来的`<a>`标签。React Router的`<Link>`组件是一个可以使用户实现导航的很棒的方式。l如，给<Link>传递一个`to`属性，可以帮助用户引导绝对路径:
```
<Link to="/about">About</Link>
```

#延伸阅读
- [<Link>](https://reacttraining.com/react-router/web/api/Link) at React Traing
- [源代码](https://github.com/ReactTraining/react-router/blob/master/packages/react-router-dom/modules/Link.js)
- [Additional props](http://knowbody.github.io/react-router-docs/api/Link.html) for the <Link> component

