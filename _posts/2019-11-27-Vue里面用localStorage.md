---
published: true
layout: post
date: '2019-11-27 13:32:20 +0300'
tags:
  - Vue
---
Vue里面用localStorage

### 写在公共JS里面
例如：`utils.js`
```
let storage = {
  set(key,value) {
    localStorage.setItem(key, JSON.stringify(value))
  },
  get(key) {
    return JSON.parse(localStorage.getItem(key))
  },
  remove(key) {
    localStorage.removeItem(key)
  }
}
module.exports = {
  storage
}
```

### 引入

```
import { storage } from "/utils.js";


export default {
  methods:{
    getGuid(){
      //获取guid的值
      storage.set('guid',false)
    },
    setGuid(){
      //设置guid的值为false
      storage.set('guid',false)
    },
  }
}
```
以上
