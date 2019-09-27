---
published: false
layout: post
date: '2019-05-21 13:32:20 +0300'
tags:
  - Vue
---
## 关于Element-UI库

### `NavMenu` 导航菜单

```
<el-menu router :default-openeds="['3']" unique-opend :default-active="$router.path">
- default-active   当前激活菜单的 index
- default-openeds   当前打开的 sub-menu 的 index 的数组
- unique-opened   是否只保持一个子菜单的展开
```
