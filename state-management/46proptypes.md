#PropTypes
PropType是一个可以让我们定义组件接收prop的数据种类，并且如果传递的数据不是正确的种类的话，就可以在调试的时候发出警告。
安装prop-types以使用它:
```
**[terminal]

npm install --save prop-types
```
下面视频展示了如何使用

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-3stateManagement-6-1.mp4{% endvideo %}
[这里是视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/a7f4728c61b539863b91752bfe21924eb81f3039)

##练习
```js
**[terminal]
import PropTypes from 'prop-types';

class Email extends React.Component {
  render() {
    return (
      <h3>Message: {this.props.text}</h3>
    );
  }
}

Email.propTypes = {
  text: // ???
};
```
>假设我们想确保有一个`text`的prop被传入，而且数据类型时字符串，那么上面`text`的值应该是什么？

#小结
总之，PropType是确保我们传入预设数据类型的有效方式。用PropTypes类型检测可以帮助我们在开发过程中定位Bug。

#延伸阅读
- [prop-types](https://www.npmjs.com/package/prop-types) library from npm
- [Typechecking With Proptypes](https://facebook.github.io/react/docs/typechecking-with-proptypes.html) from the React Docs

