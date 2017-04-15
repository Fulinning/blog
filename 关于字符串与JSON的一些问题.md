1. 使用数组拼接出如下字符串
```
var prod = {
    name: '女装',
    styles: ['短款', '冬季', '春装']
};
function getTplStr(data){
  var arr = new Array;
  arr[0]='<dl class="product">\n';
  arr[1]='\t<dt>'+data.name+'</dt>\n';
  arr[2]='\t<dd>'+data.styles[0]+'</dd>\n';
  arr[3]='\t<dd>'+data.styles[1]+'</dd>\n';
  arr[4]='\t<dd>'+data.styles[2]+'</dd>\n';
  arr[5]='</dl>';
  var str = arr.join('');
  return str;
};
var result = getTplStr(prod);  //result为下面的字符串
<dl class="product">
    <dt>女装</dt>
    <dd>短款</dd>
    <dd>冬季</dd>
    <dd>春装</dd>
</dl>
```
2. 写出两种以上声明多行字符串的方法
  - 在每一行的结束加上/，这个要注意的是/后不能有任何字符，应该让/直接接换行符才行
  - 使用+将字符连接起来，这个比较简单，但是要注意人为添加空格，不然可能不同行的字符会连在一起。
  - 利用多行注释，生成多行字符串的方法，采用toString().split('\n').slice(1,-1).join('\n')这样的方法，较为麻烦，较少使用。

3. 补全如下代码,让输出结果为字符串: hello\\饥人谷
```
var str = "hello\\\\饥人谷"
console.log(str)
```
4. 以下代码输出什么?为什么
```
var str = 'jirengu\nruoyu'
console.log(str.length)
```
输出13，因为\n只算一个字符，表示换行符，ASCII码为10

5. 写一个函数，判断一个字符串是回文字符串，如 abcdcba是回文字符串, abcdcbb不是
```
function isPlalindrome (str){
  if(str===str.split('').reverse().join('')){
    console.log(true);
  }else{
    console.log(false);
  }
}
``` 

6. 写一个函数，统计字符串里出现出现频率最多的字符
```
function maxChar(str){
  var count = 0,k=0;
  var obj = new Object;
  var max = new Array;//最大值可能有多个
  for (var i = 0;i<str.length;i++){
    if(obj[str[i]]){
      obj[str[i]]++;
    }else{
      obj[str[i]]=1;
    }
  }
  for (var key in obj){
    if(obj[key]>=count){
      count=obj[key];
      if(obj[key]>count){
        max[k]=key;
      }else{
        k++;
        max[k]=key;        
      }
    }
  }
  var str2=max.join(" ")+":"+count
  console.log(max[1])
  return str2;
} 
```

7. 写一个camelize函数，把my-short-string形式的字符串转化成myShortString形式的字符串，如
```
function camelize (str){
  var arr = str.split('-');
  for(var i=1;i<arr.length;i++){
    arr[i]=arr[i].replace(arr[i].charAt(0),arr[i].charAt(0).toUpperCase());
  }
  str2 = arr.join('');
  return str2;
}
```

8. 写一个 ucFirst函数，返回第一个字母为大写的字符 （***）
```
function ucFirst (str){
  str2=str.replace(str.charAt(0),str.charAt(0).toUpperCase());
  return str2;
}
ucFirst("hunger") == "Hunger"
```

9. 写一个函数truncate(str, maxlength), 如果str的长度大于maxlength，会把str截断到maxlength长，并加上...，如
```
function truncate(str, maxlength){
  if(str.length>maxlength){
    str=str.substr(0,maxlength)+'...';
  }
  return str;
}
truncate("hello, this is hunger valley,", 10) == "hello, thi...";
truncate("hello world", 20) == "hello world"
```

10. 什么是 json？什么是 json 语言？JSON 语言如何表示对象？window.JSON 是什么？
  - JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。它基于JavaScript（Standard ECMA-262 3rd Edition - December 1999）的一个子集。
  - JSON语言的要求是数据在名称/值对中；数据由逗号分隔；花括号保存对象；方括号保存数组；
  - JSON表示对象的方法是名称/值对组合中的名称写在前面（在双引号中），值对写在后面(同样在双引号中)，中间用冒号隔开。
  - window.JSON是用于判断浏览器是否兼容JSON的用法，IE8版本以上才内置支持JSON，IE8以下的版本要使用JSON2。
11. 如何把JSON 格式的字符串转换为 JS 对象？如何把 JS对象转换为 JSON 格式的字符串?
  - 使用JSON.parse()将字符串转换为JS对象
  - 使用JSON.stringify()将JS对象转换为JSON字符串
