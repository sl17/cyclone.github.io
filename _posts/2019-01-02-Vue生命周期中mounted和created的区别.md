---
published: false
layout: post
date: '2019-01-02 13:32:20 +0300'
tags:
  - Vue
---
## Vue生命周期中mounted和created的区别

`created`:在模板渲染成html前调用，即通常初始化某些属性值，然后再渲染成视图。
`mounted`:在模板渲染成html后调用，通常是初始化页面完成后，再对html的dom节点进行一些需要的操作。