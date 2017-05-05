1. 说说库和框架的区别？
  - 库指的是一些函数方法的集合，我们可以使用这些已经封装好的函数提高我们工作的效率，如同造房子的工具。
  - 框架指的是一种实现某个功能的框架，我们只需要往框架内填充东西，就能实现要求的功能，如同房子的设计图。
2. jquery 能做什么？
  jquery主打写的更少，做的更多。jquery提供的大量函数，极大简化了我们写JS的代码量，也使得代码简单易懂，富有逻辑性。
3. jquery 对象和 DOM 原生对象有什么区别？如何转化？
  - jquery对象只能使用jquery的方法，DOM原生对象只能使用原生JS方法
  - jquery对象加上[0]转化为DOM原生对象，用$()包裹DOM原生对象得到jquery对象
4. jquery中如何绑定事件？bind、unbind、delegate、live、on、off都有什么作用？推荐使用哪种？使用on绑定事件使用事件代理的写法？
  - 使用on()方法绑定事件
  - bind()/unbing()是jquery1.7版本之前的事件绑定方法，现在已经不推荐使用了
  - delegate()，用来执行事件委托，语法是：.delegate( selector, eventType, eventData, handler )
  - live()也是一种事件委托的方式，语法为.live( events [, data ], handler )
  - on/off是推荐的事件绑定方法，语法为.on( events [,selector ] [,data ], handler(eventObject) )
5. jquery 如何展示/隐藏元素？
  - 使用hide(a,b,c)和show(a,b,c)函数隐藏或者展示元素，a为完成隐藏或者展示所花的毫秒数，b为实现方式，Jquery提供'linear'和'swing'，c为实现后需要执行的函数
6. jquery 动画如何使用？
  - 可以使用animate(s,a,b,c)函数使用jquery动画，abc为选填项，用法同上题，s为必填项，表示的是最终的样式，动画就是由现在的样式过渡到最终的样式
  - 对于同一个元素的animate是同步的，形成一个执行队列，不同元素的animate是异步的
  - stop(true,true)方法可以立即执行完当前的动画语句，将这条语句之后的动画队列清空，而finish()将当前动画队列清空，元素返回初始位置
7. 如何设置和获取元素内部 HTML 内容？如何设置和获取元素内部文本？
	- 使用.html()的方法设置元素内部HTML内容，可读可写，括号内有值就是写，无值就是读
	- 使用.text()的方法设置元素内部文本内容，用法同上
8. 如何设置和获取表单用户输入或者选择的内容？如何设置和获取元素属性？
	- 使用.val()的方法可得到input元素中的value的值，同样可读可写
	- 使用.attr('x')的方法获得元素的x属性的值，使用.attr('x','y')方法将y赋值给元素的x属性
9. 使用 jquery实现如下效果
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <link rel="stylesheet" href="demo.css">
	<style>
		body,html {
		margin: 0;
		padding: 0;
		}
		.tab {
			margin: 8px;
			width: 200px;
		}
		.tab>ul {
			padding: 0 0 0 5px;
			background: rgb(199, 23, 30);
			color: #fff;
			list-style: none;
		}
		.tab>ul>li {
			padding: 8px;
			border-top: 1px dotted #de272e; 
			position: relative;
			cursor: pointer;
		}
		.tab li:first-child {
			border: none;
		}
		.tab li a {
			margin: 0;
			padding: 0;
			color: #fff;
			font-size: 14px;
			padding: 0 0 0 6px;
			text-decoration: none;
		}
		.tab span {
			position: relative;
			top: -3px;
			float: right;
			font-size: 18px;
		}
		.detailed-list {
			border: 1px solid #ddd;
			width: 200px;
			position: absolute;
			top: 0;
			left: 195px;
			background: #fff;
			list-style: none;
			padding: 0;
			margin: 0;
			display: none;
		}
		.detailed-list li {
			padding: 6px;
			text-align: center;
			cursor: auto;
			float: left;
			width: 70px;
			padding: 10px;
		}
		.detailed-list li a {
			color: #000;
			font-size: 14px;
		}
		.recover {
			display: block;
		}
	</style>
</head>
<body>
  <div class="tab">
    <ul>
      <li>
        <a href="#">珠宝玉器</a>
        <span>></span>
        <ul class="detailed-list">
          <li><a href="#">宝石</a></li>
          <li><a href="#">珠宝</a></li>
          <li><a href="#">翡翠</a></li>
          <li><a href="#">玛瑙</a></li>
          <li><a href="#">宝石</a></li>
          <li><a href="#">黄金</a></li>
        </ul>
      </li>
      <li>
        <a href="#">珠宝玉器</a>
        <span>></span>
        <ul class="detailed-list">
          <li><a href="#">新</a></li>
          <li><a href="#">年</a></li>
          <li><a href="#">快</a></li>
          <li><a href="#">乐</a></li>
        </ul>
      </li>
      <li>
        <a href="#">珠宝玉器</a>
        <span>></span>
        <ul class="detailed-list">
          <li><a href="#">黄鹤</a></li>
          <li><a href="#">王八蛋</a></li>
          <li><a href="#">带着</a></li>
          <li><a href="#">珠宝</a></li>
          <li><a href="#">小姨子</a></li>
          <li><a href="#">跑路了</a></li>
        </ul>
        
      </li>
      <li>
        <a href="#">珠宝玉器</a>
        <span>></span>
        <ul class="detailed-list">
          <li><a href="#">哎呀</a></li>
          <li><a href="#">我的妈</a></li>
          <li><a href="#">哇</a></li>
          <li><a href="#">宝贝</a></li>
        </ul>
      </li>
      <li>
        <a href="#">珠宝玉器</a>
        <span>></span>
        <ul class="detailed-list">
          <li><a href="#">宝石</a></li>
          <li><a href="#">黄金</a></li>
          <li><a href="#">白银</a></li>
          <li><a href="#">玛瑙</a></li>
        </ul>
      </li>
    </ul>
  </div>
  <script src="jquery-3.2.1.min.js"></script>
  <script>
		$('.tab>ul>li').on('mouseenter',function(){
			$(this).find('.detailed-list').addClass('recover');
		})
		$('.tab>ul>li').on('mouseleave',function(){
			$(this).find('.detailed-list').removeClass('recover');
		})
	</script>
</html>
</body>
```

10. 使用 jquery 实现如下效果
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <style>
		.tab {
			margin-bottom: 60px;
		}
		.tab ul {
			margin: 0;
			padding: 0;
		}
		.tab li {
			list-style: none;
		}
		.tab-head>li {
			float: left;
			border: 1px solid #aaa;
			border-left: none;
			border-right: none;
			padding: 8px 10px;
			text-align: center;
			font-size: 14px;
		}
		.tab-head>li::after {
			content: '|';
			display: inline-block;
			color: #aaa;
			font-size: 14px;
			position: relative;
			right: -12px;
		}
		.clear::after {
			content: '';
			display: block;
			clear: both;
		}
		.tab-head>li:nth-child(1) {
			border-radius: 5px 0 0 0; 
			border-left: 1px solid #aaa;
		}
		.tab-head>li:nth-child(3) {
			border-radius: 0 5px 0 0; 
			border-right: 1px solid #aaa;
		}
		.tab-head>li:hover {
			cursor: pointer;
		}
		.tab-head .active {
			background: #ddd;
			color: rgb(203, 23, 32)
		}
		.tab-content>li {
			display: none;
		}
		.tab-content .active {
			display: block;
		}
		.layout {
			width: 860px;
			border: 1px solid #aaa;
		}
		.layout li {
			list-style: none;
			float: left;
			margin-right: 23px;
			margin-bottom: 20px;
			border: 1px solid #ddd;
			position: relative;
		}
		.layout li img {
			width: 270px;
			opacity: 0.75;
		}
		.layout li p {
			padding: 16px 0 15px;
			text-align: center;
			margin: 0;
		}
		.layout li:hover {
			background: #777;
		}
		.layout li:hover::after {
			content: '立即查看';
			display: inline-block;
			font-size: 14px;
			cursor: pointer;
			padding: 8px 10px;
			background: #fff;
			border: 1px solid rgb(202, 17, 26);
			border-radius: 4px;
			color: rgb(202, 17, 26);
			position: absolute;
			top: 50%;
			left: 50%;
			transform:translate(-50%,-50%);
		}
		.layout li:nth-child(4),
		.layout li:nth-child(5),
		.layout li:nth-child(6){
			margin-bottom: 0;  
		}
		.layout ul {
			padding: 0;
			margin-right: -25px;
		} 
	</style>
</head>
<body>
  <div class="tab">
    <ul class="tab-head clear">
      <li class="active">热门</li>
      <li>珠宝首饰</li>
      <li>奢侈品</li>
    </ul>
    <ul class="tab-content">
      <li class="active">
        <div class="layout clear">
          <ul>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
          </ul>
        </div>
      </li>
      <li>
        <div class="layout clear">
          <ul>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
          </ul>
        </div>        
      </li>
      <li>
        <div class="layout clear">
          <ul>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
          </ul>
        </div>        
      </li>
    </ul>
  </div>
  <div class="tab">
    <ul class="tab-head clear">
      <li class="active">热门</li>
      <li>珠宝首饰</li>
      <li>奢侈品</li>
    </ul>
    <ul class="tab-content">
      <li class="active">
        <div class="layout clear">
          <ul>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
          </ul>
        </div>        
      </li>
      <li>
        <div class="layout clear">
          <ul>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
          </ul>
        </div>        
      </li>
      <li>
        <div class="layout clear">
          <ul>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
            <li>
              <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
                <p>风景如画</p>
            </li>
          </ul>
        </div>        
      </li>
    </ul>
  </div>
  <script src="jquery-3.2.1.min.js"></script>
  <script>
		$('.tab-head').on('click','li',function(){
			$(this).siblings('li').removeClass('active');
			$(this).addClass('active');
			var index = $(this).index();
			$(this).parent().next('ul').children().removeClass('active');
			$(this).parent().next('ul').children().eq(index).addClass('active');
		})
	</script>
</body>
</html>
```

11. 实现如下效果
```
<!doctype html>
<html>

<head>
  <meta charset="UTF-8">
  <title>ajax</title>
  <style>
    .layout {
      width: 860px;
      margin: 0 auto;
    }
    
    .layout li {
      list-style: none;
      float: left;
      margin-right: 23px;
      margin-bottom: 20px;
      border: 1px solid #ddd;
      position: relative;
    }
    
    .layout li img {
      width: 270px;
      opacity: 0.75;
    }
    
    .layout li p {
      padding: 16px 0 15px;
      text-align: center;
      margin: 0;
    }
    
    .layout li:hover {
      background: #777;
    }
    
    .layout li:hover::after {
      content: '立即查看';
      display: inline-block;
      font-size: 14px;
      cursor: pointer;
      padding: 8px 10px;
      background: #fff;
      border: 1px solid rgb(202, 17, 26);
      border-radius: 4px;
      color: rgb(202, 17, 26);
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
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
    
    .layout ul {
      margin: 0;
      padding: 0;
      margin-right: -25px;
    }
    
    .clear::after {
      content: '';
      display: block;
      clear: both;
    }
  </style>
</head>

<body>
  <div class="layout clear">
    <h1>珠宝首饰</h1>
    <ul>
      <li>
        <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
        <p>风景如画</p>
      </li>
      <li>
        <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
        <p>风景如画</p>
      </li>
      <li>
        <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
        <p>风景如画</p>
      </li>
      <li>
        <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
        <p>风景如画</p>
      </li>
      <li>
        <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
        <p>风景如画</p>
      </li>
      <li>
        <img src="http://7xpvnv.com2.z0.glb.qiniucdn.com/283a4100-10cd-4208-a3b5-4030ec03acf6" alt="">
        <p>风景如画</p>
      </li>
    </ul>
    <buttom class="btn">添加</buttom>
  </div>
  <script src="jquery-3.2.1.min.js"></script>
  <script>
    $('.btn').on('click', function () {
      $.get('/getData').done(function (data) {
        appendHtml(data);
      })
    })
    function appendHtml(data) {
      console.log(data);
      $.each(data, function () {
        var html = '';
        html += '<li>';
        html += '<img src="' + this.img + '" >';
        html += '<p>' + this.name + '</p>';
        html += '<p>' + this.price + '</p>';
        $('.layout>ul').append(html);
      })
    }
  </script>
</body>
</html>
router.js为
app.get('/getData', function(req, res) {
	var products = [
		{
			img: 'http://img10.360buyimg.com/N3/jfs/t2242/92/1446546284/374195/9196ac66/56af0958N1a723458.jpg',
			name: '珂兰 黄金手 猴哥款',
			price: '￥405.00'
		},{
			img: 'http://img10.360buyimg.com/N3/jfs/t2242/92/1446546284/374195/9196ac66/56af0958N1a723458.jpg',
			name: '珂兰 黄金转运珠 猴哥款',
			price: '￥100.00'
		},{
			img: 'http://img10.360buyimg.com/N3/jfs/t2242/92/1446546284/374195/9196ac66/56af0958N1a723458.jpg',
			name: '珂兰 黄金手链 3D猴哥款',
			price: '￥45.00'
		}
	];
	res.send(products);	
});
```