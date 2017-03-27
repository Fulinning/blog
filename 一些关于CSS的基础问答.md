1. CSS的全称是什么?
CSS的全称是层叠样式表
2. CSS有几种引入方式? link 和@import 有什么区别?
CSS有3种引入方式，分别是内联样式，内部样式，外部样式。
link是一个html标签，可以在html文件的任何地方，用来引入css样式表，即后缀名为css的文件；
@import属于css语言，在html中只能在style标签内使用@import来引入样式表。
3. 以下这几种文件路径分别用在什么地方，代表什么意思?
  - 相对路径：  
    - css/a.css  使用于link标签的href属性中或@import后的括号内，代表引入与此html文件并列的css文件夹中的a.css文件
    - ./css/a.css  使用于link标签的href属性中或@import后的括号内，与上同义
    - b.css  使用于link标签的href属性中或@import后的括号内，代表引入与此html文件并列的b.css文件
    - ../imgs/a.png  使用于img标签的src属性中，代表插入此html文件上一级文件夹中的imgs文件夹内的a.png图片
  - 绝对路径  
    - /Users/hunger/project/css/a.css  使用于link标签的href属性中或@import后的括号内，代表引入/Users/hunger/project/css/a.css这个位置的a.css文件
  - 网站路径 
     - /static/css/a.css 使用于link标签的href属性中或@import后的括号内，代表引入域名/static/css/a.css这个位置的a.css文件
    - http://cdn.jirengu.com/kejian1/8-1.png  使用于img标签的src属性中，代表插入http://cdn.jirengu.com/kejian1/8-1.png此位置的8-1.png图片
4. 如果我想在js.jirengu.com上展示一个图片，需要怎么操作?
从psd文件中使用ps的切片工具，一般将切下来的图片保存为png格式，然后使用tinypng网站进行无损压缩，最终使用img标签导入网站。当然，如果有现成的图片，就只需要压缩后用img标签导入网站。对图片而言，要在清晰度和图片大小间相互权衡，得到最优解。
5. 列出5条以上html和 css 的书写规范

html书写规范：
  - 闭合HTML标签
  - 声明正确的文档类型DOCTYPE
  - 不要使用内联样式
  - 在页面的head标签中引入所有的样式表文件。
  - 在页面底部引入JavaScript文件
  - 不要使用嵌入式JavaScript

css书写规范：
  - 语法不区分大小写，但建议统一使用小写
  - 不使用内联的style属性定义样式
  - id和class使用有意义的单词，分隔符建议使用-
  - 有可能就是用缩写
  - 属性值是0的省略单位
  - 块内容缩进
  - 属性名冒号后面添加一个空格
6. 截图介绍 chrome 开发者工具的功能区

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/5353790-253aede3968f965d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
