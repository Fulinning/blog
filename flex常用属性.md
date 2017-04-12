对块元素使用display:flex后，此元素变为弹性容器，它的子元素变为弹性项目：
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/5353790-f85e8418d663385c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
弹性容器的主要属性有：
  - flex-direction：此属性设置主轴的方向是行还是列，是顺序还是逆序，有row,row-reverse,column,column-reverse这四个常用可选值。
  - flex-wrap：此属性设置设置沿主轴方向是否需要换行，正序还是逆序，有nowrap,wrap,wrap-reverse这三个常用可选值。
  - flew-flow：由于上面两个属性总是一起使用，所以将上两个属性值合并为flex-flow属性，属性值用空格隔开。
  - justify-content：此属性设置了一行弹性项目沿主轴方向的摆放位置，靠左靠右居中或者相同边距（两边留距离）和相同距离（两边不留距离），有flex-start,flex-end,center,space-between,space-around这五个常用可选值。
  - align-items：此属性设置了一行弹性项目沿侧轴方向的摆放位置，靠左靠右或者居中，有flex-start,flex-end,center这三个常用可选值。
  - align-self：此属性设置了一个弹性项目沿侧轴方向的摆放位置，可选值与align-items类似。
  - order：此属性设置了弹性项目的排列顺序，order值支持正负值，默认为0，值越大，排列越靠后。
  - align-content：此属性设置了行与行之间的间隔，集中在顶部或底部，居中或是行与行之间保持相同距离，也可以每行周围保持相同间隔，有flex-start,flex-end,center,space-between,space-around这五个常用可选值。
