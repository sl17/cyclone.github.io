---
published: false
---
## A New Post

#### request.js

```
import Vue from "vue";
import {decorateUrl} from './utils.js'
import iView from "iview";


const doRequest=(method,url,data,header,error)=>{
  return new Promise((res,rej)=>{
    let req=null;
    if(method==='get' || method === 'delete'){
      url=decorateUrl(url,data);
      req=Vue.http.get(url,(header||{}));
    }else{
      req=Vue.http[method](url,data,(header||{}));
    }
    req.then(response=>{
      let result = response.body?response.body:response;
      if(result.success){
        res(result)
      } else if(error) {
        result.success=false
        res(result)
      } else {
        result.success=false
        iView.Message.error({
          content: result.errorMessage || '系统繁忙，请您稍后再试',
          duration: 5
        });
        res(result)
      }
    })
  })
}


const request={
  get:function({url,data,header={},error=false}){
    return doRequest('get',url,data,header,error);
  },
  post:function({url,data,header={},error=false}){
    return doRequest('post',url,data,header,error);
  },
  put:function({url,data,header={},error=false}){
    return doRequest('put',url,data,header,error);
  },
  delete:function({url,data,header={},error=false}){
    return doRequest('delete',url,data,header,error);
  },
}

module.exports ={
  request
}

```

#### utils.js

```
function decorateUrl(url, getBody={}) {
  const data=[url]
  const array=Object.keys(getBody).map(v=>`${v}=${getBody[v]}`);
  array.length>0&&data.push(array.join("&"));
  return data.join('?');
}

module.exports = {
  decorateUrl
};
```
