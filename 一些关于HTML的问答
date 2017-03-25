1. HTML、XML、XHTML 有什么区别？
  - HTML的语言要求较为宽松，语言结构较为松散。很多不严谨的语句不会被判断为错误，导致程序的可读性较差，同时也造成出现了页面问题很难找原因的情况。
  - XML是一种用于存储数据的要求较为严格的语言。不严谨的语句在XML中会被判断为错误。
  - XHTML是W3C考虑到HTML的缺点后，将HTML与XML结合而成的产物。XHTML继承了XML的优点，规范了HTML的语言结构，使HTML变得严谨起来。
2. 怎样理解 HTML 语义化？
简单来说，就是使用最能表示内容类型的标签，这使得HTML语言变得带有语义。举个例子，我想引用一句名人名言，方法1是直接在这个名人名言两边加上双引号，方法2是使用q标签，即引用标签。使用方法1明显更快捷，但它不符合HTML语义化的要求，会带来弊端。比如你在编写完HTML后想对名人名言设计样式，如果之前引用时是使用方法1，可能就要使用span标签，然后添加ID标记，才能在CSS中设置，而使用方法2，就可以直接在CSS中设置样式。再比如一些盲人使用屏幕阅读器阅读网页，使用方法2的会提醒这个内容是一个引用，而方法1则不会。
3. 怎样理解内容与样式分离的原则
内容与样式分离能使HTML与CSS各司其职，有效的减少了程序员的工作量。举个例子，公司写了几十份HTML文件都采用同一个CSS文件，突然一天，产品经理说这个样式不好，要换一个颜色。程序员只需要在那个CSS文件中简单修改就能完成。而如果内容与样式未分离，程序员就要打开几十份HTML文件逐个修改，费时费力还容易出错。
4. 有哪些常见的meta标签
  - <meta charset="utf-8"> 设置字符编码为“utf-8”
  - <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"> 设置内核渲染方式 
 - <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1"> 设置移动端的排版布局
  -  <meta name="keywords" content="前端 饥人谷">  设置关键词，方便搜索引擎检索
   - <meta name="description" content="最有爱的前端学习社区"> 设置网页描述
5. 文档声明的作用?严格模式和混杂模式指什么?<!doctype html> 的作用?
文档声明是用来说明这个HTML文件是采用什么HTML标准来编写的，浏览器通过文档声明才能明白要采用什么HTML标准来处理HTML文件，从而更好的实现页面的理解与布局。
  - 标准模式（standards mode）：浏览器根据标准规约来渲染页面。
  - 混杂模式（quirks mode）：浏览器采用更加宽松的、向后兼容的方式来渲染页面。

  <!doctype html>是文档声明的一种，用来告诉浏览器，这个HTML文件是采用HTML5的标准来编写的
6. 浏览器乱码的原因是什么？如何解决
浏览器乱码的原因是浏览器使用了与HTML文件不同的编码方式。
解决方法：在HTML的head标签内加上<meta charset="当前编码方式">
7. 常见的浏览器有哪些，什么内核
  - Internet Explorer: Trident
  - 360 Secure Browser: Trident
  - Mozilla Firefox: Gecko
  - Safari: WebKit
  - Google Chrome: Blink
  - Opera: Blink
8. 列出常见的标签，并简单介绍这些标签用在什么场景
  - h1,h2,h3 用于插入标题
  - p 用于插入段落
  - a 用于插入超链接
  - img 用于插入图片
  - q 用于插入引用
  - br 用于换行
  - ul,li 用于插入无序列表
  - ol,li 用于插入有序列表
  - dl,dt,dd 用于插入定义列表
  - div 用于创造一个区块，相当于一个容器
  - table,tr,th,td 用于插入一个HTML表格
  - em,strong 用于强调文本
  - span 相当于内联元素的div
  - iframe 用于插入一个内嵌网页
