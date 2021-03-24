---
published: false
---
## 截取

#### 两个字符之间的内容
```
'"jlkl"'.replace(/\"|\"/g,'');//jlkl

"[dsfdsf]".replace(/\[|]/g,'');//dsfdsf

```

#### 截取包前不包后（包含http or https 和 "）
```
'"http:jlkl"'.replace(/(http|https){1}:\/\/[^"'\s]*/,'');//http:jlkl


```
