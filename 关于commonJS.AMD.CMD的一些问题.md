1. 为什么要使用模块化？
  - 模块化将各个功能分隔在不同js文件中，从而具有封装性，可以重复使用，并避免了命名冲突
  - 模块化解决了加载js文件的顺序要求，以往使用script导入js文件时对导入顺序要求较高，而使用模块化的时候避免了这个问题
  - 模块化使得代码变得规范而美观
2. CMD、AMD、CommonJS 规范分别指什么？有哪些应用
  - CommonJS

    CommonJS是node端代码模块化的规范，使用js文件作为一个模块，模块内使用module.export作为被使用时候得到的值，使用模块方法为require(path/xxx)，path为合适的路径，xxx为模块名称，可省略.js，CommonJS规范使用模块时是同步调用的，适用于node服务端而不适用于浏览器
    
    例子：
    ```
    //模块定义 myModel.js

    var name = 'Byron';

    function printName(){
        console.log(name);
    }

    function printFullName(firstName){
        console.log(firstName + name);
    }

    module.exports = {
        printName: printName,
        printFullName: printFullName
    }

    //加载模块

    var nameModule = require('./myModel.js');

    nameModule.printName();
    ```
  - AMD

    AMD规范的中文为异步模块定义规范，顾名思义这个规范是异步的，可以在浏览器上使用的。使用AMD规范时需要使用requireJS作为库函数，requireJS函数中定义了define函数用于定义模块，在define中使用return来作为模块的返回值，requireJS函数中也定义了require函数用于加载并执行模块

    例子：
    ```
    // 定义模块 myModule.js
    define(['dependency'], function(){
        var name = 'Byron';
        function printName(){
            console.log(name);
        }

        return {
            printName: printName
        };
    });

    // 加载模块
    require(['myModule'], function (my){
    　 my.printName(); });
    ```
  - CMD

    CMD是国内开发的模块规范，与AMD类似。将requireJS改成了seaJS，在使用define函数时的语法不一样，加载模块时的语句是seaJS.use函数，CMD规范提倡依赖就近，即使用模块前再去加载模块，这点与commonJS类似，但CMD也属于异步加载。

    例子：
    ```
    // 定义模块  myModule.js
    define(function(require, exports, module) {
      var $ = require('jquery.js')
      $('div').addClass('active');
    });

    // 加载模块
    seajs.use(['myModule.js'], function(my){

    });
    ```
