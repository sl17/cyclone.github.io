---
published: false
---
## 关于Node

### 核心模块
- `var fs = require('fs')`：操作文件

```
var fs = require('fs')
//读取文件
fs.readFile('./test.txt',function(err, data){
  if(err){
    console.log('读取失败')
  }else{
  		console.log(data.toString())
  }
})
//编辑文件
fs.readFile('./test.txt','测试文本',function(err){
  if(err){
    console.log('编辑失败')
  }else{
    console.log('编辑成功')
  }
})

```
- `var http = require('http')`：创建web服务器

```
var http = require('http')

//创建web服务器
var server = http.createServer()

//注册request请求事件
//request 请求对象
  //请求对象可以用来获取客户端的一些请求信息,例如请求路径
//response 响应对象
  //响应对象可以用来给客户端发送响应消息
server.on('request', function(req, res){
  console.log('收到请求，路径是'+req.url)
  if(req.url == '/a'){
    //解析文本
    res.setHeader('Content-Type','text/plain; charset=utf-8')
    res.end("a页面")
  }else{
    //解析html
    res.setHeader('Content-Type','text/html; charset=utf-8')
    res.end("<p>链接是<a>点我</a></p>")
  }
})
//绑定端口，启动服务器
server.listen(3000, function(){
	console.log('启动成功')
})
```

