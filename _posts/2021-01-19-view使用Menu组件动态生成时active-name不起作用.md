---
published: false
layout: post
date: '2021-01-19 11:32:20 +0300'
tags:
  - Iview
---
## view使用Menu组件动态生成时active-name不起作用


1、给Menu组件绑定ref ,例如side_menu；
2、menu列表更新时，手动更新
　　
```
this.$nextTick(() => {
    this.$refs.side_menu.updateOpened()
    this.$refs.side_menu.updateActiveName()
})
```