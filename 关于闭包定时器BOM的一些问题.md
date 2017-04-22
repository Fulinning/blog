1. 下面的代码输出多少？修改代码让fnArr[i]() 输出 i。使用两种以上的方法
```
    var fnArr = [];
    for (var i = 0; i < 10; i ++) {
        fnArr[i] =  function(){
    	    return i;
        };
    }
    console.log( fnArr[3]() ); 
```

输出10

以下为更改后代码：
```
第一种方法：
    var fnArr = [];
    for (var i = 0; i < 10; i ++) {
      !function(i){
        fnArr[i] =  function(){
    	    return i;
        };
      }(i);
    }
    console.log( fnArr[3]() ); 
第二种方法：
    var fnArr = [];
    for (var i = 0; i < 10; i ++) {
      !function(){
        var k = i;
        fnArr[i] =  function(){
    	    return k;
        };
      }();
    }
    console.log( fnArr[3]() ); 
```

2. 封装一个汽车对象，可以通过如下方式获取汽车状态
```
var Car =(function(){
  var speed = 0;
  function setSpeed(s){
    if (typeof(s)==='number'){
      speed = s;
    }
  }
  function getSpeed(){
    return speed;
  }
  function accelerate(){
    speed += 10;
  }
  function decelerate(){
    speed -= 10;
  }
  function getStatus(){
    if (speed > 0){
      return 'running';
    }else{
      return 'stop';
    }
  }
  return {
    setSpeed: setSpeed,
    getSpeed: getSpeed,
    accelerate: accelerate,
    decelerate: decelerate,
    getStatus: getStatus,
    speed: 'error'
  }
})();

Car.setSpeed(30);
Car.getSpeed(); //30
Car.accelerate();
Car.getSpeed(); //40;
Car.decelerate();
Car.decelerate();
Car.getSpeed(); //20
Car.getStatus(); // 'running';
Car.decelerate(); 
Car.decelerate();
Car.getStatus();  //'stop';
Car.speed;  //error
```

3. 下面这段代码输出结果是? 为什么?
```
var a = 1;
setTimeout(function(){
    a = 2;
    console.log(a);
}, 0);
var a ;
console.log(a);
a = 3;
console.log(a);
```

输出1,3,2。因为setTimeout函数会将内容转移到代码执行队列的最下端，等到代码都执行完了，设置的时间到了这两个条件都满足了就执行。所以输出是1,3,2

4. 下面这段代码输出结果是? 为什么?
```
var flag = true;
setTimeout(function(){
    flag = false;
},0)
while(flag){}
console.log(flag);
```

什么都无法输出，因为setTimeout函数会将内容转移到代码执行队列的最下端，等到代码都执行完了，设置的时间到了这两个条件都满足了就执行。但是由于flag的值为true，while(flag){}为死循环，代码永远都执行不完，所以什么都不会输出。

5. 下面这段代码输出？如何输出`delayer: 0, delayer:1...`（使用闭包来实现）
```
for(var i=0;i<5;i++){
	setTimeout(function(){
         console.log('delayer:' + i );
	}, 0);
	console.log(i);
}
```

输出0,1,2,3,4,'delayer:5','delayer:5','delayer:5','delayer:5','delayer:5'
```
代码修改后为:
for(var i=0;i<5;i++){
  !function(i){
    setTimeout(function(){
          console.log('delayer:' + i );
    }, 0);
  }(i);
}
```

6. 如何获取元素的真实宽高 
  使用window.getComputedStyle('元素','伪类')[width]

  使用window.getComputedStyle('元素','伪类')[height]

7. URL 如何编码解码？为什么要编码？ 
  - 使用encodeURI(URL)、encodeURIComponent(URL)这两个函数编码，他们的区别是encodeURIComponent(URL)编码方式较为严格，会将ASCII字母、数字和~!*()'之外的所有字符编码。使用对应的decodeURI()、decodeURIComponent()这两个解码函数解码
  - 编码可以使原网址作为其他网址的一部分的时候可以不被错误的解析
8. 补全如下函数，判断用户的浏览器类型
```
function isAndroid(){
  return /Android/.test(window.navigator.userAgent);
}
funcnction isIphone(){
  return /iphone/.test(window.navigator.userAgent);  
}
function isIpad(){
  return /ipad/.test(window.navigator.userAgent);  
}
function isIOS(){
  return /iphone|ipad/.test(window.navigator.userAgent);  
}
```