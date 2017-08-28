#`componentDidMount()`事件

下面我们将要使用的生命周期事件是`componentDidMount()`

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/r4mMii8NTAQ.mp4{% endvideo %}

#`componentDidMount()`是如何工作的
上一部分讲了`componentDidMount()`事件，它是在组件添加进DOM之后立即调用的，应该在你抓取远程数据或者是做AJAX请求的时候做的，下面是React文档里对这个方法的描述
>`componentDidMount()`在组件被挂起的时候立即调用。要求DOM节点的初始化应该放在这里。如果你需要从一个远处节点加载数据，那么这里是最理想的地方。在这里Set state会出发页面的重新渲染。

下面看一个例子
```js
**[terminal]

import React, { Component } from 'react';
import fetchUser from '../utils/UserAPI';

class User extends Component {
  constructor(props) {
    super(props)

    this.state = {
      name: '',
      age: ''
    }
  }

  componentDidMount() {
    fetchUser().then((user) => this.setState({
      name: user.name,
      age: user.age
    }))
  }

  render() {
    return (
      <div>
        <p>Name: {this.state.name}</p>
        <p>Age: {this.state.age}</p>
      </div>
    )
  }
}

export default User;
```






