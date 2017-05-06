1. jQuery 中， $(document).ready()是什么意思？
  - $(document).ready()的作用是无论这行语句出现在哪里，被标记的函数会在网页完全加载完成后才执行。
  - 这个执行时机其实不算特别恰当，因为当网页图片很多时，函数也会等到所有图片加载完毕后再执行
2. $node.html()和$node.text()的区别?
  - $node.html()是获取节点内部的html语句，如节点为```<div><p>sss</p></div>```，对div使用html()得到的是```<p>sss</p>```
  - $node.text()是获取节点内部的纯文本，如节点为```<div><p>sss</p></div>```，对div使用text()得到的是sss
3. $.extend 的作用和用法? 
  - $.extend([true]obj,obj1)会将obj1的数据拷贝到obj内，若有重复的key值，则将value值覆盖，默认为浅拷贝，若第一个参数为true，则进行深拷贝
  - $.extend([true,]obj,obj1,obj2)则是先将obj1的值拷贝到obj上，再将obj2的值拷贝到obj上，原则同上
  - 还有一种写法为var obj = $.extend({},obj1,obj2)，这种写法等同于$.extend([true,]obj,obj1,obj2)，前提为obj是空对象
4. jQuery 的链式调用是什么？

jQuery的链式调用是指对一个对象连续的使用jQuery方法。提高代码可读性

5. jQuery 中 data 函数的作用
  - data函数可以将数据保存在某个节点内，方便存储和调用，语法为$node.data(key,value)或者$.data(note,key,value)，note为节点，key为名称，key的类型是字符串，value为值，类型可以是任意值。
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
$node.width();//不包括内边距宽度,仅包括内容
$node.height();//不包括内边距高度,仅包括内容
$node.innerWidth();//包括内容和内边距宽度
$node.innerHeight();//包括内容和内边距高度
$node.outerWidth();//包括内容,内边距,边框宽度
$node.outerHeight();//包括内容,内边距,边框高度
$node.outerHeight(true);//包括内容,内边距,边框,外边距高度
$node.outerWidth(true);//包括内容,内边距,边框,外边距宽度
设置就是在括号内加上值
  获取窗口滚动条垂直滚动距离
$(window).on('scroll',function(){
  console.log($(window).scrollTop())
})
  获取$node 到根节点水平、垂直偏移距离
$node.offset()
  修改$node 的样式，字体颜色设置红色，字体大小设置14px
$node.css({'color':'red';'font-size':'14px'})
  遍历节点，把每个节点里面的文本内容重复一遍
$node.each(function(){
  console.log($(this).text())
})
  从$ct 里查找 class 为 .item的子元素
$ct.find('.item')
  获取$ct 里面的所有孩子
$ct.children()
  对于$node，向上找到 class 为'.ct'的父亲，在从该父亲找到'.panel'的孩子
$node.parents('.ct').find('.panel')
  获取选择元素的数量
$node.length
  获取当前元素在兄弟中的排行
$node.index()
```

7. 用jQuery实现以下操作
```
当点击$btn 时，让 $btn 的背景色变为红色再变为蓝色
$btn.on('click',function(){
  $btn.animate({background:'red'});
  $btn.animate({background:'blue'})  
})
当窗口滚动时，获取垂直滚动距离
$(window).on('scroll',function(){
  console.log($(window).scrollTop())
})
当鼠标放置到$div 上，把$div 背景色改为红色，移出鼠标背景色变为白色
$div.on('mouseenter',function(){
  $div.css('background','red');
})
$div.on('mouseleave',function(){
  $div.css('background','white');
})
当鼠标激活 input 输入框时让输入框边框变为蓝色，当输入框内容改变时把输入框里的文字小写变为大写，当输入框失去焦点时去掉边框蓝色，控制台展示输入框里的文字
$('input').on('focus',function(){
  $('input').css('border-color','blue');
})
$('input').on('change',function(){
  $('input').val($('input').val().toUpperCase());
})
$('input').on('focusout',function(){
  $('input').css('border-color','rgb(238,238,238)');
  console.log($('input').val());
})
当选择 select 后，获取用户选择的内容
$('select').on('change',function(){
 console.log($('select').find('option:selected').text());
})
```

8. 用 jQuery ajax 实现如下效果。`当点击加载更多会加载数据

```
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <title>ajax</title>
  <style>
    div {
      text-align: center;
    }
    .data {
      margin: 0;
      padding: 0;
      list-style: none;
    }
    .data>li {
      padding: 10px;
      margin: 15px 0;
      border: 1px solid #aaa;
      border-radius: 4px;
      text-align: left;
    }
    .data>li:hover{
      background: green;
      cursor: pointer;
    }
    .btn {
      font-size: 14px;
      cursor: pointer;
      padding: 8px 10px;
      background: #fff;
      border: 1px solid rgb(202, 17, 26);
      border-radius: 4px;
      color: rgb(202, 17, 26);
    }    
  </style>
</head>

<body>
  <div>
    <ul class="data">
      <li>内容1</li>
      <li>内容2</li>
    </ul>
    <buttom class="btn">加载更多</buttom>
  </div>
  <script src="jquery-3.2.1.min.js"></script>
  <script>
    var index = 3,length = 5;
    $('.btn').on('click',function(){
      $.get('/getData',{index:index,length:length}).done(function(data){
        appendHTML(data);
        index+=length;
      })
    })
    function appendHTML(data){
      console.log(data)
      var str =''
      $.each(data,function(){
        str += '<li>'+this+'</li>'
      })
      $('.data').append(str);
    }
  </script>
</body>
</html>
```

router.js为

```
app.get('/getData', function(req, res) {
	index = req.query.index;
	length = req.query.length;
	data = [];
	str = '';
	for (var i = index;i<parseInt(index)+parseInt(length);i++){
		str = '内容'+i;
		data.push(str);
	}
	res.send(data);	
});
```