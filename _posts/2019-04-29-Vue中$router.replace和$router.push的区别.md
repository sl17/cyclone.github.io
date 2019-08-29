---
published: false
---
## Vue中$router.replace和$router.push的区别

### $router.push
>这个方法会向 history 栈添加一个新的记录，当用户点击浏览器后退按钮时，则回到之前的 URL。

### $router.replace

>这个方法***不***会向 history 栈添加一个新的记录。

```
//这样写的也不会有浏览记录
this.$router.push({path: '/Msite', replace: true})
//如果是声明式就是像下面这样写：
<router-link :to="..." replace></router-link>
// 编程式:
router.replace(...)
````



```
<div  @click="goTo('/Msite')"></div>

methods:{
  goTo(path){
    console.log(this.$router.replace(path))
    //console.log(this.$router.push(path))
  }
}
```
