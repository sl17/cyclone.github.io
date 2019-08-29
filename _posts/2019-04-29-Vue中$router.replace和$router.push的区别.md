---
published: false
---
## Vue中$router.replace和$router.push的区别

### $router.push
>这个方法会向 history 栈添加一个新的记录，当用户点击浏览器后退按钮时，则回到之前的 URL。

### $router.replace

>这个方法***不***会向 history 栈添加一个新的记录。


```
<div  @click="goTo('/Msite')"></div>

methods:{
  goTo(path){
    console.log(this.$router.replace(path))
    //console.log(this.$router.push(path))
  }
}
```

