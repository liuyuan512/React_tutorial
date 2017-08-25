#React仅仅是JavaScript

React其实就是普通的JavaScript。

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/FTSYIXx2R10.mp4{% endvideo%}


在过去的几年中，函数式编程对JavaScript生态系统和社区产生了巨大的影响。函数式编程是JavaScript中的一个高级主题，并且有数百本书籍。要深入了解功能编程的好处需要更加系统的学习函数式编程。而React建立在函数式编程技术的许多技术上。然而，有几个重要的JavaScript函数对于函数式编程至关重要，我们应该深入了解一下。它们是**.map（）**和**.filter（）**方法。
下面深入看一下**.map()**和**.filter()**数组方法
#数组的.map()方法
JavaScript的数组方法[Array .map() method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map),通过数组调用，返回一个基于作为参数传递的函数的一个新的数组。我们看一下这个例子:


```js
const names = ['Michael', 'Ryan', 'Tyler'];

const nameLengths = names.map( name => name.length );
```
我们看一下发生了什么。.map()方法只能作用于数组，因此我们开始开始于一个数组


```
const names = ['Michael', 'Ryan', 'Tyler'];
```


我们在names数组上调用.map()方法，并且给这个方法传递一个函数作为参数


```js
names.map( name => name.length );
```
作为参数传递给.map()函数的箭头函数会作用于names数组里面的而每一个元素。箭头函数接收数组里的第一个元素作为实参，赋值给形参变量name，返回它的长度值。接着它对数组里剩下的两个元素执行相同的操作。
.map()返回一个新的数组，这个数组里存储着来自作为参数传递的函数的返回值


```
const nameLengths = names.map( name => name.length );
```

所以nameLengths将会是一个新的数组[7,4,5]。理解这一点很重要。**.map()方法返回一个新数组，它并不改变原来的数组。**

这里只是简单的介绍一下.map()函数是如何工作的，更深的研究，点击[.map() on MDN.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
##.map()测试
#####用提供的musicData数组和.map()方法创建一个新的数组，这个数组的形式应该是`<name> by <artist> sold <sales> copies`。将这个新的数组存储在数组albumSalesStrings里面。比如albumSalesStrings数组的第一个元素应该是"25 by Adele sold 1731000 copies"

> 使用 `musicData` 数组 and `.map()`方法:
    - 对于数组里面的每一个元素都返回如下形式的字符串
      <album-name> by <artist> sold <sales> copies
    - 将返回的数据存储在一个新的变量albumSalesStrings里
>```
const musicData = [
    { artist: 'Adele', name: '25', sales: 1731000 },
    { artist: 'Drake', name: 'Views', sales: 1608000 },
    { artist: 'Beyonce', name: 'Lemonade', sales: 1554000 },
    { artist: 'Chris Stapleton', name: 'Traveller', sales: 1085000 },
    { artist: 'Pentatonix', name: 'A Pentatonix Christmas', sales: 904000 },
    { artist: 'Original Broadway Cast Recording', 
      name: 'Hamilton: An American Musical', sales: 820000 },
    { artist: 'Twenty One Pilots', name: 'Blurryface', sales: 738000 },
    { artist: 'Prince', name: 'The Very Best of Prince', sales: 668000 },
    { artist: 'Rihanna', name: 'Anti', sales: 603000 },
    { artist: 'Justin Bieber', name: 'Purpose', sales: 554000 }
];
```
>你的答案:


#数组的.filter()方法
JavaScript的[Array .filter() method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)和.map()方法是相似的
- 由数组调用
- 以函数作为参数
- 返回一个新数组 

不同在于作为参数传递给filter()方法的函数是一个筛选条件，只有数组里的元素满足这个筛选条件的才会被存储到新返回的数组里面。下面看一个例子


```js
const names = ['Michael', 'Ryan', 'Tyler'];

const shortNames = names.filter( name => name.length < 5 );

```

和上面一样，我们开始有一个数组：

`const names = ['Michael', 'Ryan', 'Tyler'];`

我们在数组names上面调用filter()方法，并且给它传递一个函数作为参数

`names.filter( name => name.length < 5 );`

那么和上面一样，就像作为参数给.map()函数传递的函数一样，传递给filter()方法的函数会被names数组里面的每一个元素调用。比如看第一个元素，是'Michael'被存储在name变量里面。然后对这个元素执行测试，它检查name变量的长度是否小于5.如果大于5，则跳过执行下一元素(这个元素就不会被存储在返回的新数组里面)。如果小于5，那么`name.length<5`返回`true`并且这个元素被包含在新返回的数组里。
最后，就像.map()函数一样，.filter()方法返回了一个新的数组，但是没有修改原来的数组:
```
const shortNames = names.filter( name => name.length < 5 );
```
所以结果就是`shortNames`数组为['Ryan'].它只有一个元素，因为`'Michael'` 和 `'Tyler'`的长都比5要大，被我们过滤出去了。
这只是一个简单的介绍`.filter()`的工作原理的，详细的研究点击[.filter() on MDN.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

##.filter()测试
#####利用提供的`musicData`数组和`.filter()`方法来创建一个新的数组，这个新数组只包含name属性的长度在10和25之间的元素。将新数组存储在`results`里面

> 使用 `musicData` 数组 and `.filter()`方法:
    - 返回一个新数组，新数组只包含name属性的长度在10和25之间的元素
    - 将返回的数据存储在一个新的变量`results`里

>```
const musicData = [
{ artist: 'Adele', name: '25', sales: 1731000 },
{ artist: 'Drake', name: 'Views', sales: 1608000 },
{ artist: 'Beyonce', name: 'Lemonade', sales: 1554000 },
{ artist: 'Chris Stapleton', name: 'Traveller', sales: 1085000 },
{ artist: 'Pentatonix', name: 'A Pentatonix Christmas', sales: 904000 },
{ artist: 'Original Broadway Cast Recording',
name: 'Hamilton: An American Musical', sales: 820000 },
{ artist: 'Twenty One Pilots', name: 'Blurryface', sales: 738000 },
{ artist: 'Prince', name: 'The Very Best of Prince', sales: 668000 },
{ artist: 'Rihanna', name: 'Anti', sales: 603000 },
{ artist: 'Justin Bieber', name: 'Purpose', sales: 554000 }
];
```
你的答案:

#组合`.map()`和`.filter()`
让`.map()`和`.filter()`很厉害的地方在于他们可以组合起来。因为这两个方法都返回的是一个数组，所以我们可以把这两个方法连起来调用。
```
const names = ['Michael', 'Ryan', 'Tyler'];

const shortNamesLengths = names.filter( name => name.length < 5 ).map( name => name.length );
```
首先names数组被过滤后返回一个新数组，然后`.map()`方法又被这个返回的新数组调用,接着再返回一个新数组。这个新返回的数组被存储在了`shortNamesLengths`数组里面。

##.filter()和.map()组合测试
#####使用`musicData`这个数组和`.filter()`和`.map()`这两个方法，filter和map这个数组，把结果存在一个`popular`的变量里。先用`.filter()`过滤售卖专辑超过1000000张的元素，然后对返回的数组调用`.map()`方法变成这个格式:
```
<artist> is a great performer
```
比如第一个popular数组里的元素应该是`Adele is a great performer`

> 使用 `musicData` 数组 ， `.filter()`和`.map()`方法:
    - 对数组先用.filter()方法，返回一个新数组，新数组包含售卖专辑超过1000000张的元素
    - 将返回的新数组调用.map()方法，返回的元素盈是这个样式<artist> is a great performer
    - 将返回的数组存储在一个新的变量popular里

>```
const musicData = [
{ artist: 'Adele', name: '25', sales: 1731000 },
{ artist: 'Drake', name: 'Views', sales: 1608000 },
{ artist: 'Beyonce', name: 'Lemonade', sales: 1554000 },
{ artist: 'Chris Stapleton', name: 'Traveller', sales: 1085000 },
{ artist: 'Pentatonix', name: 'A Pentatonix Christmas', sales: 904000 },
{ artist: 'Original Broadway Cast Recording',
name: 'Hamilton: An American Musical', sales: 820000 },
{ artist: 'Twenty One Pilots', name: 'Blurryface', sales: 738000 },
{ artist: 'Prince', name: 'The Very Best of Prince', sales: 668000 },
{ artist: 'Rihanna', name: 'Anti', sales: 603000 },
{ artist: 'Justin Bieber', name: 'Purpose', sales: 554000 }
];
```
你的答案：

#小结
React只是创建了一些JavaScript。你无需再学习一个特殊的字符模板或者一个新的方式。
以后将会用到两个常用的方法：
- `.map()`
- `.filter()`

习惯这两个方法很重要，可以花些时间练习一下如何使用它们。可以试着把一些for循环用`.map()`实现以下。也可以将一些if语句用`.filter()`方法代替