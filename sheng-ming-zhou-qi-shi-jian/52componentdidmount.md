#`componentDidMount()`事件

下面我们将要使用的生命周期事件是`componentDidMount()`

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-4RenderUIwithExternalData-2-1.mp4{% endvideo %}

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

这个组件有一个`componentDidMount()`生命周期事件。我们看一下这个组件是如何工作的:
  1. render()方法被调用的时候，会更新页面，添加一个含有name的段落和age的段落的`<div>`。但是需要了解的是，一开始的时候`this.state.name`和`this.state.age`是空值，也就是说页面并不会有数据。
  2. 一旦组件被挂起，生命周期事件`componentDidMount()`就会被触发
    1. 来自`UserAPI`的`fetchUser`请求会被调用，将会给用户的数据库发送请求
    2. 当数据返回，`setState()`被调用，并且更新`name`和`age`。 
  3. 一旦state发生变化，render()就会再次被调用。这会重新渲染页面，但是此时`this.state.name`和`this.state.age`就有值了。
  
下面将使用`componentDidMount()`来抓取在服务器里面的真实数据
>!要求的文件!
 项目最初有直接克隆项目和从最初的[create-react-app](https://github.com/facebookincubator/create-react-app)自己来实现，如果你是使用了create-react-app来构建的项目，那么你需要这个文件[the ContactsAPI file](https://github.com/udacity/reactnd-contacts-complete/blob/master/src/utils/ContactsAPI.js)
 
{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-4RenderUIwithExternalData-2-2.mp4{% endvideo %}
[这里是视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/2f165b6f1c95092722486249b00cb172bcf1d3ab)

#移除Contacts
到目前为止，我们开始从Contacta API抓取数据，并且将它们添加进`this.state.contacts`。但是还没有移除功能。目前当我们移除一个contact的时候，仅仅是从`this.state.contacts`中里面移除，但是它仍然存在与后端数据库里。下面使用Contacts API's `remove()`方法来更新后端

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-4RenderUIwithExternalData-2-3.mp4{% endvideo %}
[视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/151ea430aea71230811cd395ee08398df9b8f170)

>如果误删了所有的数据，你只需要重新启动后端服务器


#小结
`componentDidMount()`是React提供的大量生命周期事件中的其中之一。`componentDidMount()`会在组件被挂起的时候被调用。如果你需要动态的抓取数据或者运行AJAX请求，那么你需要在`componentDidMount()`里面去做这些事情。

#延伸阅读
- [componentDidMount()](https://facebook.github.io/react/docs/react-component.html#componentdidmount)from the React Docs



