#使React如此特殊的地方
- 组合特性
- 声明式属性
- 由父组件传向子组件的数据流方向
- React只是一些JavaScript代码而已

###可以延伸阅读一下
- [Virtual DOM](https://facebook.github.io/react/docs/optimizing-performance.html#avoid-reconciliation)。Virtual DOM(虚拟DOM)映射了一个对应节点都是HTML元素的树。React通过遍历执行这个虚拟DOM的操作，使得我们的应用从真实的DOM的繁杂的操作中解放出来
- [The Diffing Algorithm](https://facebook.github.io/react/docs/reconciliation.html#the-diffing-algorithm)。Diffing决定了如何对DOM做出有效的改变。利用Diffing，旧的DOM节点会被拿掉并且会在需要的时候替换成新的。通过这个方式，我们的应用就不需要执行一些不必要的操作来计算什么时候需要渲染内容了。
