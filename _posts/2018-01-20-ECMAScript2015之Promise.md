---
published: false
---
## 关于Promise

### get请求

```
export function get(url, params){    
  return new Promise((resolve, reject) =>{        
    axios.get(url, {            
      params: params        
    }).then(res => {
      resolve(res.data);
    }).catch(err =>{
      reject(err.data)        
    })    
  });
}
```
### post请求

```
export function post(url, params) {
  return new Promise((resolve, reject) => {
    axios.post(url, qs.stringify(params))
    .then(res => {
      resolve(res.data);
    })
    .catch(err =>{
      reject(err.data)
    })
  });
}
```

## 实际使用
在main.js中引入js

```
import {get,post} from './utils/api'
//将方法挂载到Vue原型上
Vue.prototype.get = get;
Vue.prototype.post = post;
```

#### 这是请求聚合数据的接口为列子

```
this.get('/toutiao/index?type=top&key=秘钥',{})
  .then((res)=>{
    if(res.error_code===0){
      resolve(res);
    }else{
      //这里抛出的异常被下面的catch所捕获
      reject(error);
    }
  })
  .catch((err)=>{
    console.log(err)
  })
 ```
 
 
 
#### 使用promise

1.比如用户想请求url1接口完后再调url2接口

```
var promise = new Promise((resolve,reject)=>{
  let url1 = '/toutiao/index?type=top&key=秘钥'
  this.get(url,{})
  .then((res)=>{
    resolve(res);
  })
  .catch((err)=>{
    console.log(err)
  })
});
promise.then((res)=>{
  let url2 = '/toutiao/index?type=top&key=秘钥'
  this.get(ur2,{})
  .then((res)=>{
    //只有当url1请求到数据后才会调用url2，否则等待
    resolve(res);
  })
  .catch((err)=>{
    console.log(err)
  })
})
```

### Promise对象

#### Promise有三种状态

- pending: 等待中，或者进行中，表示还没有得到结果
- resolved: 已经完成，表示得到了我们想要的结果，可以继续往下执行
- rejected: 也表示得到结果，但是由于结果并非我们所愿，因此拒绝执(用catch捕获异常)

### Promise基本用法

#### Promise.all()用法

```
var p = Promise.all([p1, p2, p3]);
```

#### Promise.race()用法
>一个待定的 Promise 只要给定的迭代中的一个promise解决或拒绝，就采用第一个promise的值作为它的值

```
var p = Promise.race( [p1,p2,p3] )
```









