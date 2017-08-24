#其它框架的数据绑定

前端框架像[Angular](https://angular.io/)和[Ember](https://emberjs.com/)都是利用了数据的双向绑定。在双向的属性绑定里，App里的数据总是同步的，不管它是在哪里更新。如果在model里更改了数据，那么View里数据也会更新。或者，如果用户在view里更新了数据，那么数据也会在model里更新。双向流的数据绑定很强大，但是这也使应用更难推理，更难知道到底数据是在哪里进行的更新。

#延伸阅读
- [Angular's two-way data binding](https://angular.io/guide/template-syntax#!#two-way)
- [Ember's two-way data binding](https://guides.emberjs.com/v2.13.0/object-model/bindings/)

#React的数据流

在React里，数据的流向是单一的。数据只能从父组件流向子组件

![](/assets/data-flow.jpg)
在这张图片里，我们有两个组件:
- 父组件
- 子组件

数据存储在父组件里并且只能流向子组件。虽然数据存在于父组件，但是父组件和子组件都能够访问数据。然而如果数据需要被更新，那么只有父组件能够执行更新。如果子组件需要更改数据，那么它需要把更改好的数据发送给父组件，在父组件里完成数据的更新。然后更好的数据会从父组件再传给子组件。
这看起来好像多做了很多额外的工作，但是单一数据流和只能在一个地方修改数据使我们更容易理解这个应用的工作方式。

##练习1
>一个**FlightPlanner**组件里存储了预定机票的信息。它里面包含了两个子组件**DatePickerh**和**DestinationPicker** 


>```js
<FlightPlanner>
  <DatePicker />
  <DestinationPicker />
</FlightPlanner>
```
>如果这是一个React应用，那么哪一个组件应该负责更新数据呢？

>- **FlightPlanner**
>- **DatePickerh**
>- **DestinationPicker** 


##练习2
>现在我们假定**FlightPlanner**组件有两个子组件:**LocationPicker** 和 **DatePicker**。 而**LocationPicker**组件还有两个子组件**OriginPicker** 和 **DestinationPicker**
>如果下面的代码是一个React应用，那么那一部分应该负责更新数据呢?
>```js
<FlightPlanner>
  <LocationPicker>
    <OriginPicker />
    <DestinationPicker />
  </LocationPicker>
  <DatePicker />
</FlightPlanner>
```
>- **FlightPlanner**
>- **DatePickerh**
>- **DestinationPicker** 
>- **OriginPicker**
>- **DestinationPicker**

#小结
在React里，数据只能向一个方向流动。如果数据需要在兄弟组件里共享，那么这个数据就应该存储在父组件里，并且传递给需要这个数据的子组件里。

