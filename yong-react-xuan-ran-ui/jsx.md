#嵌套元素
我们看一下如果元素需要嵌套应该怎么做

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/JRkpQamCWxI.mp4{% endvideo %}
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/PDT3A1L1sPs.mp4{% endvideo %}

#`.createElement()`只能返回一个根元素
因为`React.createElement( /* type */, /* props */, /* content */ )`只能创建一种特定的React元素，通常就传递一个`<div>`或者`<span>`标签来表示React元素的类型，这里的`content`属性其实可以是任何内容，也就是说可以再嵌套一个React元素
```
const element = React.createElement('div', null,
  React.createElement('strong', null, 'Hello world!')
);
```
当这个React元素作为HTML被渲染时，'Hello world'被嵌套在了一个<div>标签里。也就是说我们可以深层嵌套，但是注意最后的调用一定只能是返回一个单个元素

JSX的由来

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/9kyaEeKDUGE.mp4{% endvideo %}


下面我们把`React.createElement()`替换成JSX
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/h_rHa8mVyBk.mp4{% endvideo %}

#练习
给一个JSX：
```
const greeting = (
  <div className='greeting'>
    <h2>Hello world!</h2>
  </div>
);
```

如果我们想要输出同样的HTML，那么空白处需要依次填写什么内容?
```
const greeting = React.createElement(
  __1__,
  { className: 'greeting' },
  React.createElement(
    __2__,
    {},
    __3__
  )
);
```