#生命周期事件
当我们需要管理或者处理来自数据库或者其它地方的数据时，就需要调用AJAX方法来获取数据，可是这个方法应该在哪里执行呢？你或许会把它放在`render()`函数里面，但是,`render()`函数是不应该有任何副作用的，它应该是一个纯函数。这个函数里面不能够处理任何异步的进程。它只能够就收`props`，返回一个UI的描述。这些事情应该在生命周期事件里调用
{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-4RenderUIwithExternalData-1-1.mp4{% endvideo %}

#render()函数只能用来渲染页面
这里需要再强调一下，数据的远程抓取不应该放在render()函数里面。组件的render()函数应该只是用来渲染这个组件，不应该包含任何的HTTP的请求，抓取数据或者修改DOM。render()方法同样也不可以调用其他的方法来做这些事情。
我们将需要做像AJAX请求的这些代码放到生命周期事件里去

#Lifecycle Events

生命周期事件是组件里的特殊方法。这些方法自动绑定在组件的实例中，并且React会在组件的生命周期里的特定时刻调用特定的方法。有很多生命周期事件，下面列举一些常用的事件

- `componentWillMount()`
 > 在组件被插入DOM之前立即调用

- `componentDidMount()` 
 > 在组件插入DOM之后立即调用
 
- `componentWillUnmount()`
 > 在组件从DOM里移除之前立即调用
 
- `componentWillReceiveProps()`
 > 每当组件将要接受新的props时立即调用
 
如果要使用以上函数，只需要在组件中创建同名函数，React会自动调用。这是绑定React组件不同生命生命周期的最容易实现的方式。

