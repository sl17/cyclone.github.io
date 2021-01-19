## iview使用Menu组件动态生成时active-name不起作用

1、给Menu组件绑定ref ,例如side_menu；
2、menu列表更新时，手动更新
　　
```
this.$nextTick(() => {
    this.$refs.side_menu.updateOpened()
    this.$refs.side_menu.updateActiveName()
})
```
