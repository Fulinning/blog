1. class 和 id 的使用场景?
同一个html文件中，id的值不能相同，class的值可以相同，这决定了他们的性质。
id用来标记整个文件中具有独一无二意义的标签；
而class用来标记整个文件中具有同一类意义的标签。
2. CSS选择器常见的有几种?
  - 基础选择器
  - 组合选择器
  - 属性选择器
  - 伪类选择器
  - 伪元素选择器
3. 选择器的优先级是怎样的?对于复杂场景如何计算优先级？
优先级排列为：
  1. 在属性后面使用 !important 会覆盖页面内任何位置定义的元素样式
  2. 作为style属性写在元素标签上的内联样式
  3. id选择器
  4. 类选择器
  5. 伪类选择器
  6. 属性选择器
  7. 标签选择器
  8. 通配符选择器
  9. 浏览器自定义

  计算优先级方法：
将行内样式 <div style="xxx"></div>标记为a，ID 选择器标记为b，类，属性选择器和伪类选择器标记为c，标签选择器、伪元素标记为d，根据abcd的个数统计abcd的值，用比较4位数的值来比较abcd的值，值大的优先级高。
4. a:link, a:hover, a:active, a:visited 的顺序是怎样的？ 为什么？
顺序为：a:link,a:visited,a:hover,a:active
因为css中有一个规则，当标签的优先级相同时，采用排列在最后的标签样式。
要防止a:visited的样式覆盖a:hover,a:active的样式，所以a:visited应该在它们前面，同理a:hover应该在a:active前面。
5. 以下选择器分别是什么意思?
``` 
#header{
}    选择id为header的元素
.header{
}    选择class为header的元素
.header .logo{
}    选择class为header的元素的子元素中class为logo的元素
.header.mobile{
}    选择class同时为header和mobile的元素
.header p, .header h3{
}    选择class为header的元素的p和h3子元素
#header .nav>li{
}    选择id为header的元素的子元素中class为nav的子元素li
#header a:hover{
}    选择id为header的元素的子元素a的鼠标悬停状态
#header .logo~p{
}    选择id为header的元素的子元素中class为logo的元素之后的同级p元素
#header input[type="text"]{
}    选择id为header的元素的子元素input中type="text"的元素
```
6. 列出你知道的伪类选择器
  - E:link	匹配所有未被点击的链接
  - E:visited	匹配所有已被点击的链接
  - E:active	匹配鼠标已经其上按下、还没有释放的E元素
  - E:hover	匹配鼠标悬停其上的E元素
  - E:focus	匹配获得当前焦点的E元素
  - E:enabled	匹配表单中可用的元素
  - E:disabled	匹配表单中禁用的元素
  - E:checked	匹配表单中被选中的radio或checkbox元素
  - E::selection	匹配用户当前选中的元素
  - E:nth-child(n)	匹配其父元素的第n个子元素，第一个编号为1
  - E:nth-of-type(n)  与:nth-child()作用类似，但是仅匹配使用同种标签的元素
7. div:first-child和div:first-of-type的作用和区别
  - div:first-child：选择所有div元素的父元素的第一个子元素
  - div:first-of-type：选择所有div元素的父元素的第一个div子元素
  区别就是div:first-of-type比div:first-child多了一个特定的标签限制
8. 运行如下代码，解析下输出样式的原因。
```
<style>
.item1:first-child{
  color: red;
}
.item1:first-of-type{
  background: blue;
}
</style>
 <div class="ct">
   <p class="item1">aa</p>
   <h3 class="item1">bb</h3>
   <h3 class="item1">ccc</h3>
 </div>
```
首先，.item1:first-child选择器选择了所有class="item"的元素的父元素的第一个子元素，不管是p元素还是h3元素，它们的父元素div的第一个子元素都是p元素，所有p元素应用了样式，字体变为红色。
其次，.item1:first-of-type选择器选择了所有class="item"的元素的父元素的第一个同种标签的子元素，具体到类， <p class="item1">aa</p>选择了它的父元素div的第一个标签为p的子元素，即选中了它自己，<h3 class="item1">bb</h3>选择了它的父元素div的第一个标签为h3的子元素，即选中了它自己,<h3 class="item1">ccc</h3>选择了它的父元素div的第一个标签为h3的子元素，即选中了<h3 class="item1">bb</h3>，所有最后是aa和bb应用了样式：背景色为蓝色。
