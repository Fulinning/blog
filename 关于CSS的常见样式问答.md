1. 块级元素和行内元素分别有哪些？动手测试并列出4条以上的特性区别
  - 块级元素：h1,h2,h3,h4,h5,h6,p,div,form,table,tr,th,td,ul,li,ol,dl,dt,dd,br
  - 行内元素：span,em,a,imp,input,strong,br,select,button
特性区别：
  - 块级元素不管内容有多少会将区域占满一整行，而行内元素不会
  - 块级元素可以设置高度和宽度，而行内元素不行
  - 块级元素设置margin,padding时盒模型正常扩展，而行内元素设置margin,padding时盒模型只有左右正常扩展，上下的区域不扩展，只有边框和背景音乐可以应用
  - 块级元素能包含块级元素和行内元素，而行内元素只能包含行内元素
  - 在有元素应用了浮动样式时，块级元素正常布局，而块级元素内的行内元素在布局时会考虑浮动样式，从而绕开它布局
2. 什么是 CSS 继承? 哪些属性能继承，哪些不能？
CSS继承指的是父元素应用的某些样式会“继承”给子元素，使子元素具有同样的样式。颜色，字体，行高，文本样式能继承；边框，内外边距无法继承。我认为属性继承挺人性化的，很多时候你认为它应该能继承，它就能继承，你任务它不应该去继承，它就不继承。
3. 如何让块级元素水平居中？如何让行内元素水平居中?
块级元素继承：对块级元素继承：margin: 0 auto;
行内元素继承：对行内元素的父元素使用：text-align: center;
4. 用 CSS 实现一个三角形
http://js.jirengu.com/qujitasuze/1/edit
5. 单行文本溢出加 ...如何实现?
  white-space: nowrap;  这行代表超出文本不换行
  overflow: hidden;  这行代表超出文本隐藏
  text-overflow: ellipsis;  这行代表如果有超出文本用...显示
6. px, em, rem 有什么区别
  - px就是最基本的设置像素
  - em：x em对于font-size来说就是父元素字体大小的x倍，对于除了font-size的属性来说就是当前元素的字体大小的x倍
  - rem：x rem指的是body元素字体大小的x倍
7. 解释下面代码的作用?为什么要加引号? 字体里\5b8b\4f53代表什么?
```
body{
  font: 12px/1.5 tahoma,arial,'Hiragino Sans GB','\5b8b\4f53',sans-serif;
}
```
说明body字体大小为12px，行高为各元素字体大小的1.5倍，字体系列tahoma,arial,'Hiragino Sans GB','\5b8b\4f53',sans-serif从头到尾依次选择。
因为有空格可能会被误认为多种字体，所以加上引号。
\5b8b\4f53是unicode码，这样写防止外国人的电脑不适配或者编码方式不同，\5b8b\4f53翻译成中文是黑体的意思。
