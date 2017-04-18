1. 写一个函数，返回从min到max之间的 随机整数，包括min不包括max 
```
function randomNumber (min,max,num){
  var arr = []
  for(var i = 0 ;i < num ;i++){
    arr[i]=parseInt(Math.random()*(max-min)+min);
  }
  return arr;
}
```

2. 写一个函数，返回从min都max之间的 随机整数，包括min包括max 
```
function randomNumber (min,max,num){
  var arr = []
  for(var i = 0 ;i < num ;i++){
    arr[i]=parseInt(Math.random()*(max-min+1)+min);
  }
  return arr;
}
```
3. 写一个函数，生成一个长度为 n 的随机字符串，字符串字符的取值范围包括0到9，a到 z，A到Z。
```
function getRandStr (len){
  var dict = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
  var str = '';
  for(var i = 0 ;i < len ;i++){
    str += dict[parseInt(Math.random()*62)];
  }
  return str;
}
var str = getRandStr(10); // 0a3iJiRZap
```

4. 写一个函数，生成一个随机 IP 地址，一个合法的 IP 地址为 0.0.0.0~255.255.255.255
```
function getRandIP(){
  var arr = [];
  for(var i = 0 ;i < 4 ;i++){
    arr[i] = parseInt(Math.random()*256);
  }
  str = arr.join('.');
  return str;
}
var ip = getRandIP()
console.log(ip) // 10.234.121.45
```
5、写一个函数，生成一个随机颜色字符串，合法的颜色为#000000~ #ffffff
```
function getRandColor(){
  var dict = '0123456789abcdef'
  var arr = [];
  for(var i = 0 ;i < 6 ;i++){
    arr[i] = dict[parseInt(Math.random()*16)];
  }
  str = '#'+arr.join('')
  return str;
}
var color = getRandColor()
console.log(color)   // #3e2f1b
```

数组任务

1. 数组方法里push、pop、shift、unshift、join、splice分别是什么作用？用 splice函数分别实现push、pop、shift、unshift方法
  - push(x): 将x从数组的末尾插入数组
  - pop(): 将数组的最后一个成员移出数组
  - shift(): 将数组的第一个成员移出数组
  - unshift(x): 将x从数组的开头插入数组
  - join('x'): 将数组各成员以x连接生成字符串，默认为逗号
  - splice(x,y,z): 从数组的第x个成员开始进行y位的替换，替换内容为z
  - 用splice实现push(x): arr.splice(arr.length,0,x)
  - 用splice实现pop(): arr.splice(arr.length-1,1)
  - 用splice实现shift(): arr.splice(0,1)
  - 用splice实现unshift(x): arr.splice(0,0,x)
  
2. 写一个函数，操作数组，数组中的每一项变为原来的平方，在原数组上操作
```
function squareArr(arr){
  for(var i = 0; i<arr.length;i++){
    arr[i]=arr[i]*arr[i];
  }
}
var arr = [2, 4, 6]
squareArr(arr)
console.log(arr) // [4, 16, 36]
```

3. 写一个函数，操作数组，返回一个新数组，新数组中只包含正数，原数组不变
```
function filterPositive(arr){
  newArr = [];
  for(var i = 0;i<arr.length;i++){
    if(typeof(arr[i])=='number'&&arr[i]>0){
      newArr.push(arr[i]);
    }
  }
    return newArr;
}
var arr = [3, -1,  2,  '饥人谷', true]
var newArr = filterPositive(arr)
console.log(newArr) //[3, 2]
console.log(arr) //[3, -1,  2,  '饥人谷', true
```

Date 任务

1. 写一个函数getChIntv，获取从当前时间到指定日期的间隔时间
```
function getChIntv(str){
  var timeEnd = new Date(str);
  var timeStart = new Date();
  var timeLength = new Date(timeEnd-timeStart);
  console.log(timeLength);
  var timeDate = parseInt(timeLength.getTime()/(1000*60*60*24));
  var timeHour = timeLength.getHours();
  var timeMinute = timeLength.getMinutes();
  var timeSecord = timeLength.getSeconds();
  var str = '据'+str+'还有'+timeDate+'天'+timeHour+'小时'+timeMinute+'分钟'+timeSecord+'秒'
  return str ;
}
var str = getChIntv("2018-02-08");
console.log(str);  // 距除夕还有 20 天 15 小时 20 分 10 秒
```

2. 把hh-mm-dd格式数字日期改成中文日期
```
function getChsDate(str){
  var dict = ['零','一','二','三','四','五','六','七','八','九','十','十一','十二','十三','十四','十五','十六','十七','十八','十九','二十','二十一','二十二','二十三','二十四','二十五','二十六','二十七','二十八','二十九','三十','三十一']
  var arr = str.split('-');
  var year = dict[arr[0][0]]+dict[arr[0][1]]+dict[arr[0][2]]+dict[arr[0][3]]+'年';
  var month = dict[parseInt(arr[1])+'']+'月';
  var date = dict[parseInt(arr[2])+'']+'日';
  var str = year+month+date;
  return str ;
}
var str = getChsDate('2015-01-08');
console.log(str);  // 二零一五年一月八日 
```

3. 写一个函数，参数为时间对象毫秒数的字符串格式，返回值为字符串。假设参数为时间对象毫秒数t，根据t的时间分别返回如下字符串:
```
刚刚（ t 距当前时间不到1分钟时间间隔）
3分钟前 (t距当前时间大于等于1分钟，小于1小时)
8小时前 (t 距离当前时间大于等于1小时，小于24小时)
3天前 (t 距离当前时间大于等于24小时，小于30天)
2个月前 (t 距离当前时间大于等于30天小于12个月)
8年前 (t 距离当前时间大于等于12个月)
function friendlyDate(time){
  var timeStart = new Date(parseInt(time));
  var timeEnd = new Date();
  timeLength = timeEnd - timeStart;
  if (parseInt(timeLength/(1000*60*60*24*365))!=0){
    return parseInt(timeLength/(1000*60*60*24*365))+'年前';
  }else if (parseInt(timeLength/(1000*60*60*24*30))!=0){
    return parseInt(timeLength/(1000*60*60*24*30))+'个月前';    
  }else if (parseInt(timeLength/(1000*60*60*24))!=0){
    return parseInt(timeLength/(1000*60*60*24))+'天前';    
  }else if (parseInt(timeLength/(1000*60*60))!=0){
    return parseInt(timeLength/(1000*60*60))+'小时前';    
  }else if (parseInt(timeLength/(1000*60))!=0){
    return parseInt(timeLength/(1000*60))+'分钟前';    
  }else{
    return '刚刚';    
  }
}
var str = friendlyDate( '1484286699422' ) //  1分钟前
var str2 = friendlyDate('1483941245793') //4天前
console.log(str);
console.log(str2);
```