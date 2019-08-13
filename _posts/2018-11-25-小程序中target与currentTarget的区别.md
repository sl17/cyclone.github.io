---
published: false
---
### 小程序中target与currentTarget的区别


```
html:

<view class='nav' catchtap="titlepage" data-speechTitle="{{title3}}">
...
</view>



script:

titlepage(e) {
    console.log(e.currentTarget.dataset.speechtitle)
}
```
1、如果绑定的事件所在组件没有子元素，则用e.target===e.currentTarget一样；

2、如果事件绑定在父元素中，且该父元素有子元素，当用e.currentTarget时，不管点击父元素所在区域还是子元素（当前事件），都正确执行， 
若用e.target时，点击父元素所在区域无错，点击子元素区域，执行报错
>报错的原因是事件没绑定在子元素上，是在父元素上，子元素要用e.currentTarget才正确！