#嵌套元素
我们看一下如果元素需要嵌套应该怎么做

{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/JRkpQamCWxI.mp4{% endvideo %}
{% video %}https://s3.cn-north-1.amazonaws.com.cn/u-vid-hd/PDT3A1L1sPs.mp4{% endvideo %}

#`.createElement()`只能返回一个根元素
因为`React.createElement( /* type */, /* props */, /* content */ )`只能创建一种特定的React元素，通常就传递一个`<div>`或者`<span>`标签来表示React元素的类型，但是