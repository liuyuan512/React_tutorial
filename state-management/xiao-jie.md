#小结
当涉及到追踪应用中的数据，想一下你将会用这个数据做什么，并且当用户和你的应用交互的时候数据会有什么反应。如果你想要你的组件存储一个不变的本地数据，就考虑使用`state`来存储这个信息。在大多情况下，state将会用来管理组件里的controlled form元素。

另一方面，如果这个数据你希望是只读属性，就用`props`代替。state和props通常都是以对象的形式存在，改变他们中的任意一个都会引发组件的重新渲染，但是他们扮演者不同的作用。
供你延伸阅读的一些资料:
- [Thinking in React](https://facebook.github.io/react/docs/thinking-in-react.html)
- [Functional Components vs. Stateless Functional Components vs. Stateless Components](https://tylermcginnis.com/functional-components-vs-stateless-functional-components-vs-stateless-components/)
- [Controlled Components](https://facebook.github.io/react/docs/forms.html)