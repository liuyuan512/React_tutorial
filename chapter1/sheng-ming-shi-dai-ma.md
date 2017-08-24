#命令式代码

很多的JavaScript都是**命令式代码（imperative code）**。如果你不清楚“命令式"的含义，你也许会困惑。
当我们写的JavaScript是声明式的时候，我们会告诉JavaScript具体**做什么**和**怎么做**。把它想成我们要给JavaScript去执行每一步的具体的命令。例如这个**for**循环


```js
const people = ['Amanda', 'Geoff', 'Michael', 'Richard', 'Ryan', 'Tyler']
const excitedPeople = []

for (let i = 0; i < people.length; i++) {
  excitedPeople[i] = people[i] + '!'
}
```

在这段代码里，我们遍历**people**数组中的每一个元素，将每个元素的值后面添加上一个感叹号，然后把这个新的字符串存贮在**excitedPeople**数组里面。
这就是_命令式_代码。我们不得不给它每一步的命令:
- 为循环指数设定一个初始值- (let i = 0)
- 告诉for循环什么时候停止循环- (i < people.length)
- 拿到i数组i位置的值并且加上’!’- (people[i] + '!')
- 把这个数据存储到数组的i个位置- (excitedPeople[i])
- 让i的值增加1- (i++)

告诉一个函数每一步它需要做的事情并不理想，所以我们要改善成声明式代码

#声明式代码
与命令式代码对应的是**声明式代码(declarative code)**用声明式代码，我们不需要告诉JavaScript每一个具体的执行步骤就可以得到想到结果。相反，我们直接**声明(declare)**我们想要的结果，JavaScript会负责执行它。我们看个例子，把上面的for循环函数重构成声明式的代码
可以先思考一下，在命令式代码中，我们执行每一步得到了最后的结果。那么最终我们想要的结果是什么呢？刚开始我们拿到的是一个组数

```js
const people = ['Amanda', 'Geoff', 'Michael', 'Richard', 'Ryan', 'Tyler']
```

我们最终的目标还是得到一个相熟名字的数组，但是需要在每个名字的后面加上感叹号


```js
["Amanda!", "Geoff!", "Michael!", "Richard!", "Ryan!", "Tyler!"]
```

为了得到这结果，我们只需要使用JavaScript的**.map()**函数来声明我们想要的结果就可以了


```js
const excitedPeople = people.map(name => name + '!')
```
对，这就是声明式代码。在这段代码里，我们没有做的是:
- 创建一个迭代器i
- 告诉代码什么时候需要停止循环
- 利用迭代器i来访问**prople**数组里面每一个元素的值
- 将每一个新的字符串存在**excitedPeople**数组里面
所有的这些步骤都被包含在JavaScript的**.map()**数组方法里面

##练习题
下面的这个代码是命令式的还是声明式的？


```js
const people = ['Amanda', 'Geoff', 'Michael', 'Richard', 'Ryan', 'Tyler']
const longNames = people.filter(name => name.length > 6)
```


>.map()和.filter()方法会在”React只是JavaScript“部分有详细介绍

#React是声明式的
先看一下React是怎样实现声明式特性的


```js
<button onClick={activateTeleporter}>Activate Teleporter</button>
```
第一次看起来似乎很奇怪，这是有效的React代码，并且应该很容易理解。注意button只有一个**onClick**属性。我们没有用**.addEventListener()**来设立一个事件来处理一系列步骤。相反，我们只是声明当点击按钮的时候我们想要**activateTeleporter**函数运行。
#声明式代码小结
命令式代码需要指示JavaScript具体怎么执行每一个步骤，而用声明式代码，我们只需要告诉JavaScript我们想要的结果，让JavaScript去操心具体的执行步骤。
React是声明式的因为我们只需要写出我们想要的，React会负责处理我们的声明式代码并且执行JavaScript/DOM的每一个步骤以得到我们想要的结果。
#延伸阅读
- [Imperative vs Declarative Programming](https://tylermcginnis.com/imperative-vs-declarative-programming/)
- [Difference between declarative and imperative in React.js?](https://stackoverflow.com/questions/33655534/difference-between-declarative-and-imperative-in-react-js)

