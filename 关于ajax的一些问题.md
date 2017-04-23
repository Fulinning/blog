1. ajax 是什么？有什么作用？
  - ajax是一个由XMLHttpRequest对象提供的一些关于不刷新页面，更新页面信息的技术，这个对象提供了一系列的方法实现了这样的技术。
  - ajax可以发送一条请求，使页面的一些局部的信息更新，而不刷新整个页面。这样的方法减少了响应时间，也提高了页面效率。
2. 前后端开发联调需要注意哪些事情？后端接口完成前如何 mock 数据？
  - 前后端开发联调需要注意的有：
    1. 使用的方式是'get'还是'post'
    2. 使用的URL是什么
    3. 前端将会传送给后端什么数据，参数名及作用
    4. 后端需要给前端返回什么样的经过处理的数据
  - 使用router.js去伪造一个后端，在router.js内使用事先约定好的数据类型传送数据方式来模拟是否功能可以正确使用
3. 点击按钮，使用 ajax 获取数据，如何在数据到来之前防止重复点击?
```
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
</head>
<body>
  <ul class="news">
  </ul>
  <button id="btn">加载更多</button>   
  <script>
    var btn = document.querySelector('#btn');
    var news = document.querySelector('.news');
    var index = 0;
    var ready = true;
    btn.addEventListener('click', function(){
       if(!ready){
         return ;
       }
       var xhr = new XMLHttpRequest()
       xhr.onreadystatechange = function(){
         if(xhr.readyState === 4 && (xhr.status === 200 || xhr.status === 304)){
          var data = JSON.parse(xhr.responseText)
          render(data)
          ready = true;
         }
       }
      xhr.open('get', '/getMore?index=' + index + '&length=5', true)
      xhr.send()
      index += 5;
      ready = false;
    })
    function render(data){
      var ct = document.createDocumentFragment()
      for(var i = 0; i < data.length; i++){
        var node = document.createElement('li')
        node.innerText = data[i]
        ct.appendChild(node)
      }
      news.appendChild(ct)
    }
  </script>
  
</body>
</html>

router.js为
app.get('/getMore', function(req, res) {
  var index = parseInt(req.query.index);
  var length = req.query.length;
	var data = [];
	for (var i= 0 ; i<length;i++){
		data.push('新闻'+(index+i))
	}
	res.send(data);		
});
```

4. 封装一个 ajax 函数，能通过如下方式调用。后端在本地使用server-mock来 mock 数据
```
function ajax(opts){
  opts.url = opts.url||'';
  opts.data = opts.data||{};
  opts.type = opts.type||'get';
  opts.success = opts.success||function(){};
  opts.error = opts.error||function(){};
  var xhr = new XMLHttpRequest()
  xhr.onreadystatechange = function(){
    if(xhr.readyState === 4){
      if(xhr.status === 200 || xhr.status === 304){
        var ret = JSON.parse(xhr.responseText)
        opts.success(ret);
      }else{
        opts.error();
      }
    } 
  }
    var str = '';
    for(var key in opts.data){
      str = str + key + '=' + opts.data.key +'&'
    }
    str = str.substr(0,str.length-1)
  if(opts.type==='get'){
    xhr.open(opts.type, opts.url+'?'+str, true)
    xhr.send()
  }
  if(opts.type==='post'){
    xhr.open(opts.type, opts.url , true)
    xhr.setRequestHeader('Content-type','application/x-www-form-urlencoded')
    xhr.send(str)        
  }
}

document.querySelector('#btn').addEventListener('click', function(){
    ajax({
        url: '/login',   //接口地址
        type: 'get',               // 类型， post 或者 get,
        data: {
            username: 'xiaoming',
            password: 'abcd1234'
        },
        success: function(ret){
            console.log(ret);       // {status: 0}
        },
        error: function(){
           console.log('出错了')
        }
    })
});
```