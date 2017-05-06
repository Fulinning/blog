1. jQuery 中， $(document).ready()是什么意思？
  - $(document).ready()的作用于原生JS中window.onload意义相同，无论这行语句出现在哪里，被标记的函数会在网页完全加载完成后才执行。
  - 这个执行时机其实不算特别恰当，因为当网页图片很多时，函数也会等到所有图片加载完毕后再执行
2. $node.html()和$node.text()的区别?
  - $node.html()是获取节点内部的html语句，如节点为<div><p>sss</p></div>，对div使用html()得到的是<p>sss</p>
  - $node.text()是获取节点内部的纯文本，如节点为<div><p>sss</p></div>，对div使用text()得到的是sss
3. $.extend 的作用和用法? 
  - $.extend([true]obj,obj1)会将obj1的数据拷贝到obj内，若有重复的key值，则将value值覆盖，默认为浅拷贝，若第一个参数为true，则进行深拷贝
  - $.extend([true,]obj,obj1,obj2)则是先将obj1的值拷贝到obj上，再将obj2的值拷贝到obj上，原则同上
  - 还有一种写法为var obj = $.extend({},obj1,obj2)，这种写法等同于$.extend([true,]obj,obj1,obj2)，前提为obj是空对象
题目4： jQuery 的链式调用是什么？
题目5： jQuery 中 data 函数的作用
6. 写出以下功能对应的 jQuery 方法：
```
给元素 $node 添加 class active，给元素 $noed 删除 class active
$node.addClass('active')  $node.removeClass('active')
展示元素$node, 隐藏元素$node
$node.show()  $node.hide()
获取元素$node 的 属性: id、src、title， 修改以上属性
获取：$node.attr('id')  $node.attr('src')   $node.attr('title')
修改：$node.attr('id','xxx')  $node.attr('src','xxx')   $node.attr('title','xxx')
给$node 添加自定义属性data-src
$node.attr('data-src','xxx')
在$ct 内部最开头添加元素$node
$ct.prepend($node)
在$ct 内部最末尾添加元素$node
$ct.append($node)
删除$node
$node.remove()
把$ct里内容清空
$ct.empty()
在$ct 里设置 html <div class="btn"></div>
$ct.html('<div class="btn"></div>')
获取、设置$node 的宽度、高度(分别不包括内边距、包括内边距、包括边框、包括外边距)
$node.css('width')
$node.css('height')
获取窗口滚动条垂直滚动距离
获取$node 到根节点水平、垂直偏移距离
修改$node 的样式，字体颜色设置红色，字体大小设置14px
遍历节点，把每个节点里面的文本内容重复一遍
从$ct 里查找 class 为 .item的子元素
获取$ct 里面的所有孩子
对于$node，向上找到 class 为'.ct'的父亲，在从该父亲找到'.panel'的孩子
获取选择元素的数量
获取当前元素在兄弟中的排行
```

题目7：

用jQuery实现以下操作
当点击$btn 时，让 $btn 的背景色变为红色再变为蓝色
当窗口滚动时，获取垂直滚动距离
当鼠标放置到$div 上，把$div 背景色改为红色，移出鼠标背景色变为白色
当鼠标激活 input 输入框时让输入框边框变为蓝色，当输入框内容改变时把输入框里的文字小写变为大写，当输入框失去焦点时去掉边框蓝色，控制台展示输入框里的文字
当选择 select 后，获取用户选择的内容
题目8： 用 jQuery ajax 实现如下效果。`当点击加载更多会加载数据展示到页面效果预览144