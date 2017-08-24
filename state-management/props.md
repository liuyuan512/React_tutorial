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

此视频中修改的代码

>###练习

 如果有一个<Clock />组件，如何传递currentTime prop？

 - <Clock {new Data().getTime()} />

 - <Clock this.props={new Data().getTime()} />

 - <Clock currentTime={new Data().getTime()} />

 - <Clock this.currentTime={new Date().getTime()} />

 

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/qkKNrTUvGJU.mp4{% endvideo %}

此视频中修改的代码

>###练习

对于这个组件<Clock />:

<Clock currentTime='3:41pm'>如何在组件内部访问值3:41pm?

- Clock.currentTime

- currentTime

- this.currentTime

- this.props.currentTime

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/mnIuUk9cexA.mp4{% endvideo %}

此视频中修改的代码

>如果你电脑上的程序没有政策运行，检查你的两个服务器是否都有打开

>###练习

 你如何向一个组件传递两个不容的props?

 - <Clock time={Date.now()} zone='MST' />

 - <Clock props={{time:Date.now(),zone='MST'}} />

 - <Clock [time=Date.now(),zone='MST'] />

 - <Clock props={[Date.now(),'MST']}>

##小结

prop是你向组件传递传递的任何输入，就像HTML的属性一样，prop名字和值可以被添加到组件里。

```js

// passing a prop to a component

<LogoutButton text='Wanna log out?' />

```

在这个例子里，text是prop，字符串'Wanna log out?'是value.

所有的props都被存在了this.props的对象里。所以从组件内部访问这个text prop,得这样表达this.props.text:

```

// access the prop inside the component

render() {

    return <div>{this.props.text}</div>

}

```

#延伸阅读

- Components and Props from the React Docs
