---
published: false
layout: post
date: '2021-01-14 13:32:20 +0300'
tags:
  - JS操作
---
## 截取

#### 两个字符之间的内容
```
'"jlkl"'.replace(/\"|\"/g,'');//jlkl

"[dsfdsf]".replace(/\[|]/g,'');//dsfdsf

```

#### 截取包前不包后（包含并且开始是`http or https` 不包含并且结尾是`"`）
```
'"http:jlkl"'.replace(/(http|https){1}:\/\/[^"'\s]*/,'');//http:jlkl

```

#### 截取包前不包后（包含并且开始是`http or https` 不包含并且结尾是`" or &`）
```
'"http:jlkl"'.replace(/(http|https){1}:\/\/[^"'\s|(&)]*/,'');//http:jlkl
```
