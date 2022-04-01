---
published: true
layout: post
date: '2022-04-01 13:32:20 +0300'
tags:
  - JS
---
## JS中callback回调的写法

```
function a(callback){
	// 请求结束调用 b()
	console.log('aaaa');
	if(typeof callback == 'function'){
		callback()
	}
}
function b(){
	// 请求结束调用 
	console.log('bbbb');
}
a(b)
a(()=>{b()})
```
