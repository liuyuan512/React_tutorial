#Props

父组件与子组件之间可以用props属性来相互通信

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/10YRWO2e7Y8.mp4{% endvideo %}

下个视频你需要复制的数组:
```js
const contacts = [
  {
    "id": "ryan",
    "name": "Ryan Florence",
    "email": "ryan@reacttraining.com",
    "avatarURL": "http://localhost:5001/ryan.jpg"
  },
  {
    "id": "michael",
    "name": "Michael Jackson",
    "email": "michael@reacttraining.com",
    "avatarURL": "http://localhost:5001/michael.jpg"
  },
  {
    "id": "tyler",
    "name": "Tyler McGinnis",
    "email": "tyler@reacttraining.com",
    "avatarURL": "http://localhost:5001/tyler.jpg"
  }
]
```
#确保两个服务器都在运行

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/v3hF0cyPo3M.mp4{% endvideo %}

[此视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/664306f50a05aafe47f4109860e00593fcbf0321)

>###练习
 如果有一个`<Clock />`组件，如何传递`currentTime prop`？

 

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/qkKNrTUvGJU.mp4{% endvideo %}
[此视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/eaa138af7d992f05449f524d514ac4224f736ae4)

>###练习
对于这个组件`<Clock />`:
`<Clock currentTime='3:41pm'>`如何在组件内部访问值`3:41pm`?
- Clock.currentTime
- currentTime
- this.currentTime
- this.props.currentTime

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/mnIuUk9cexA.mp4{% endvideo %}
[此视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/43add2a640214483b00d9ca491990bb86104501e)

>如果你电脑上的程序没有政策运行，检查你的两个服务器是否都有打开

>###练习
 你如何向一个组件传递两个不容的props?


##小结
`prop`是你向组件传递传递的任何输入，就像HTML的属性一样，`prop`名字和值可以被添加到组件里。

```js
// passing a prop to a component
<LogoutButton text='Wanna log out?' />
```
在这个例子里，`text`是`prop`，字符串`'Wanna log out?'`是value.

所有的props都被存在了`this.props`的对象里。所以从组件内部访问这个`text prop`,得这样表达`this.props.text`:

```
// access the prop inside the component

render() {
    return <div>{this.props.text}</div>
}

```

#延伸阅读
- [Components and Props](https://facebook.github.io/react/docs/components-and-props.html) from the React Docs