---
published: true
layout: post
date: '2020-07-25 11:32:20 +0300'
tags:
  - Css
---
## Input的placeholder属性相关

```
/*input在显示placeholder的内容的时候，边框呈粉色，placeholder内容呈红色*/
input:placeholder-shown {
  border: 1px solid pink;
}
input::placeholder{
  color: red;
}
```

[传送门](https://sl17.github.io/layout/demo11.html)
