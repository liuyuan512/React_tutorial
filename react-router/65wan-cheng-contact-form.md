#创建Contact Form
现在页面创建联系人的部分还是空的。下面我们在这个页面上添加创建联系人的表单，就可以增加我们自己的联系人了。

>##要求的文件
>在项目之处，你有选择克隆我们的starter 项目，或者用`create-react-app`从头开始自己写,如果你还没有添加这个文件[the ImageInput.js file](https://github.com/udacity/reactnd-contacts-complete/blob/master/src/ImageInput.js)，你需要添加上。

ImageInput组件是一个自定义的<input>,它可以在以数据URL的形式提交给服务器之前，动态的读取和重新规定图片文件大小。它同样也可以看图片的预览。如果你有兴趣，可以深入研究一下这部分

{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-5ManagingAppLocation-6-1.mp4{% endvideo %}
[这里是视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/09d3d6da0fa0e2c40c95c66d99d0a2d31323ae06)

#序列化表单数据
到这里，我们的表单将会序列化用户的输入(比如:`name`和`email`),将他们作为一个查询字符串添加到URL。通过序列化这些表单输入，我们可以添加额外的一些功能。最终我们希望这个应用可以处理添加联系人并且保存到state里面。
我们需要用[form-serialize](https://www.npmjs.com/package/form-serialize)包来使它作为JavaScript对象来输出，以供应用使用。
```
**[terminal]
npm install --save form-serialize
```
下面看一下具体怎么实现
{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-5ManagingAppLocation-6-2.mp4{% endvideo %}
[视频中修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/554bab12367719b1526900ea27b8bb60237aba0d)

#将新的联系人更新到服务器
我们拿到了联系人表单。序列化数据以后将它传递到父组件。我们需要做的是有一个功能完整的app来保存联系人到服务器端。
{% video %}http://ovwbdgz95.bkt.clouddn.com/react-fundamental-5ManagingAppLocation-6-3.mp4{% endvideo %}
[这里是视频里修改的代码](https://github.com/udacity/reactnd-contacts-complete/commit/6ea0a9abe23c06465447bc2b0366e6c794eaefbf)

