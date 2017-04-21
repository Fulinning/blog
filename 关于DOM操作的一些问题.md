1. dom对象的innerText和innerHTML有什么区别？
  - innerText会获取此元素对象的内的所有文本并连接起来
  - innerHTML会获取此元素对象内的所有标签加文本并连接起来
2. elem.children和elem.childNodes的区别？
  - elem.children会得到一个由elem的子元素节点组成的数组
  - elem.children会得到一个由elem的子元素节点以及子文本节点组成的数组  
3. 查询元素有几种常见的方法？ES5的元素选择方法是什么?
  - 有getElementById()、getElementsByClassName()、getElementsTagName()、getElementsByName()这几种常用的方法，通过ID名、类名、标签类型、Name值来查询元素
  - ES5开始新增了querySelector()、querySelectorAll()这样的方法，通过提供选择器的值来查询元素
4. 如何创建一个元素？如何给元素设置属性？如何删除属性
  - 使用createElement()创建一个元素
  - 使用setAttribute(attribute,value)的方法给元素设置属性
  - 使用removeAttribute(attribute)的方法删除元素的属性
5. 如何给页面元素添加子元素？如何删除页面元素下的子元素?
  - 使用appendChild()的方法给页面元素添加子元素
  - 使用removeChild()的方法删除页面元素的子元素
6. element.classList有哪些方法？如何判断一个元素的 class 列表中是包含某个 class？如何添加一个class？如何删除一个class?
  - add(class1, class2, ...)在元素中添加一个或多个不存在的类名
  - contains(class)返回布尔值，判断指定的类名是否存在
  - item(index)返回索引值对应的元素类名。index的值从0开始，在区间范围外则返回null
  - remove(class1, class2, ...)移除元素中一个或多个类名，移除不存在的类名，不会报错
  - 使用contains(class)的方法判断class列表中是包含某个class
  - 使用add(class)方法添加一个class
  - 使用remove(class)方法删除一个class
7. 如何选中如下代码所有的li元素？ 如何选中btn元素？
```
<div class="mod-tabs">
   <ul>
       <li>list1<li>
       <li>list2<li>
       <li>list3<li>
   </ul>
   <button class="btn">点我</button>
</div>

a = getElementByTagName(li);
b = getElementsByClassName(btn)[0]
```