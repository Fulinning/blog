this 相关问题
1. apply、call 、bind有什么作用，什么区别
  - apply、call、bind的作用是可以在指定函数作用域(this值)运行函数
  - apply、call、bind的语法结构都是xxx(a,b)，这里xxx指的是apply、call、bind中的任意一个，a指的是函数作用域(即this值)，b指的是参数，接下来细说
  - 对于call，如xxx.call(a,b)的作用为xxx这个函数在this值为a的环境下运行，接受的参数列表为b，b的形式要写成x1,x2,x3这样
  - 对于apply，如xxx.apply(a,b)的作用为xxx这个函数在this值为a的环境下运行，接受的参数列表为b，b必须是一个数列，apply和call的区别就是这里
  - 对于bind，如xxx.apply(a,b)的作用为绑定this值和参数，原理是bind会创建一个以a为this值，b为参数的新函数去替代原先的函数，b是可选的，如不写就只绑定this值
  
2. 以下代码输出什么?
```
var john = { 
  firstName: "John" 
}
function func() { 
  alert(this.firstName + ": hi!")
}
john.sayHi = func
john.sayHi()
```

  - 输出john: hi!
  - 因为john.sayHi = func这条语句将func赋值给了john对象下的函数，之后采用john.sayHi()这样的形式去调用，this的值就是john对象，所以输出的是john: hi!

3. 下面代码输出什么，为什么
```
func() 
function func() { 
  alert(this)
}
```

  - 输出[object Window]
  - 因为在全局作用域调用函数，this指向全局对象window，之后要alert，会使用toString方法，得到[object Window]

4.下面代码输出什么
```
document.addEventListener('click', function(e){
    console.log(this);
    setTimeout(function(){
        console.log(this);
    }, 200);
}, false);
```

  - 输出document和window对象
  - 在事件处理函数中的this代表的是绑定这个事件的DOM对象，而在setTimeout内的this指的是全局对象window

5.下面代码输出什么，why
```
var john = { 
  firstName: "John" 
}

function func() { 
  alert( this.firstName )
}
func.call(john)
```

  - 输出John
  - func.call(john)这句话中的call指定了本次调用func函数中的this值为john，所以输出的是john.firstName，也就是John

6. 以下代码有什么问题，如何修改
```
var module= {
  bind: function(){
    $btn.on('click', function(){
      console.log(this) //this指什么
      this.showMsg();
    })
  },
  
  showMsg: function(){
    console.log('饥人谷');
  }
}
```

  - 由于在事件处理函数内this的值变为了$btn，而不是module
  - 可以在事件处理函数后加上.bind(module)，将事件处理函数的this值绑定为module

原型链相关问题
7. 有如下代码，解释Person、 prototype、__proto__、p、constructor之间的关联。
```
function Person(name){
    this.name = name;
}
Person.prototype.sayName = function(){
    console.log('My name is :' + this.name);
}
var p = new Person("若愚")
p.sayName();
```

  - Person是一个构造函数，构造函数有自己的原型函数，原型函数也是一个构造函数，函数中的属性和方法可以被派生函数继承，对于Person来说，Person.prototype就是Person的原型函数，而每个原型函数又都有一个constructor属性，如Person.prototype.constructor的值为Person，这个属性是用来分辨原型对象到底属于哪个构造函数。如现在使用构造函数Person创建了一个p对象，p对象内有一个__proto__属性，用来包含构造函数Person的原型函数的属性和方法，这之内就有一个属性是constructor，用来指向Person，所以可以得到p.constructor === Person为true

8. 上例中，对对象 p可以这样调用 p.toString()。toString是哪里来的? 画出原型图?并解释什么是原型链。
  - 对对象调用一个方法时，如在对象内部找不到方法，会到对象的原型内去找方法，如果原型内找不到，就会到原型的原型内找方法，直到找到原型链的尽头，也就是none
  - toSring()方法在p.__proto__.__proto__中可发现
  - 原型链指的是原型能继承另一个原型的方法，而前面所说的另一个原型又能继承再另一个原型的方法，形成一层类似链条的结构，称为原型链。
  ![image.png](http://upload-images.jianshu.io/upload_images/5353790-4ae2bd8d70d01a68.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
9. 对String做扩展，实现如下方式获取字符串中频率最高的字符
```
var str = 'ahbbccdeddddfg';
var ch = str.getMostOften();
console.log(ch); //d , 因为d 出现了5次

String.prototype.getMostOften = function(){
  var arr = this.split('')
  var obj = {}
  var max = 0;
  for(var i =0; i<arr.length; i++){
    if(obj[arr[i]]){
      obj[arr[i]]++;
    }else{
      obj[arr[i]] = 1;
    }
  }
  for (var key in obj) {
    if(obj[key] > max){
      max = obj[key]
    }
  }
  return max;
}
```

10. instanceOf有什么作用？内部逻辑是如何实现的？
  - instanceOf可以判断这个对象是否由这个构造函数的原型派生而成
  - instanceOf会将对象的__proto__与构造函数的prototype比对，看是否相等，相等就返回true，如果不等，则将对象的__proto__.__proto__再去与构造函数的prototype去比对，直到__proto__.__prito__为null
继承相关问题
11. 继承有什么作用?

  - 继承后的子对象将拥有父对象的全部属性和方法，且父对象的属性方法改变之后，所有的子对象内的未覆盖的对应属性和方法也会改变。
  - 继承可以节省内存，减少代码长度，也更加符合逻辑，同时也更加方便。

12. 下面两种写法有什么区别?
```
//方法1
function People(name, sex){
    this.name = name;
    this.sex = sex;
    this.printName = function(){
        console.log(this.name);
    }
}
var p1 = new People('饥人谷', 2)

//方法2
function Person(name, sex){
    this.name = name;
    this.sex = sex;
}

Person.prototype.printName = function(){
    console.log(this.name);
}
var p1 = new Person('若愚', 27);
```

  - 从只创建一个对象上来说，是没有什么区别的。但是一旦创建了多个对象，第二种写法的优越性就能体现出来。
  - 假如创建了5个Person对象，对于第一种写法，就要创建5个一模一样的函数，而对于第二种写法，则只需要创建一个函数，能够节省内存空间
  - 并且如果哪天printName代码需要修改，第二种写法只需要改原型就可以，而第一种写法需要一个对象一个对象的去改

13. Object.create 有什么作用？兼容性如何？
  - Object.create()方法使用指定的原型对象和其属性创建了一个新的对象。即Object.create(a)则创建了一个以a作为原型对象的对象。
  - Object.create()方法是ES5的方法，在IE9及以上才能使用

14. hasOwnProperty有什么作用？ 如何使用？
  - hasOwnProperty()方法能判断括号内的属性或方法是否是对象本身的还是属于对象的原型对象里的。
  - 如a为一个对象，a.hasOwnProperty(b)就能判断出b是否是a本身的属性或方法还是属于a的原型对象里的属性或方法。  
15. 如下代码中call的作用是什么?
```
function Person(name, sex){
    this.name = name;
    this.sex = sex;
}
function Male(name, sex, age){
    Person.call(this, name, sex);    //这里的 call 有什么作用
    this.age = age;
}
```

call的作用是使用Male作为this，name、sex作为参数执行一遍函数Person，这样就把函数内部的属性或方法继承过来了

16. 补全代码，实现继承 
```
function Person(name, sex){
  this.name = name;
  this.sex = sex;
}

Person.prototype.getName = function(){
  console.log(this.name)
};    

function Male(name, sex, age){
  Person.call(this, name, sex);
  this.age = age;
}

Male.prototype = Object.create(Person.prototype)
Male.prototype.getAge = function(){
    console.log(this.age)
};

var ruoyu = new Male('若愚', '男', 27);
ruoyu.printName();
```