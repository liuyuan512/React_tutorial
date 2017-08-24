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
 - `<Clock {new Data().getTime()} />`
 - `<Clock this.props={new Data().getTime()} />`
 - `<Clock currentTime={new Data().getTime()} />`
 - `<Clock this.currentTime={new Date().getTime()} />`
 

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/qkKNrTUvGJU.mp4{% endvideo %}
[此视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/eaa138af7d992f05449f524d514ac4224f736ae4)

>###练习
对于这个组件`<Clock />`:
`<Clock currentTime='3:41pm'>`如何在组件内部访问值`3:41pm`?
- Clock.currentTime
- currentTime
- this.currentTime
- this.props.currentTime


