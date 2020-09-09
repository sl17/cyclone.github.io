---
published: true
layout: post
date: '2020-09-09 18:36:20 +0300'
tags:
  - Vue
---
## Vue里关于html2canvas组件

`useCORS:true,//（图片跨域相关）`
`allowTaint:false,//允许跨域（图片跨域相关）`


# 将网络图片转化为base64

```
convertImgToBase64(url, callback, outputFormat){
  var canvas = document.createElement('CANVAS'),
  ctx = canvas.getContext('2d'),
  img = new Image;
  img.crossOrigin = 'Anonymous';
  img.onload = function(){
    canvas.height = img.height;
    canvas.width = img.width;
    ctx.drawImage(img,0,0);
    var dataURL = canvas.toDataURL(outputFormat || 'image/jpg');
    callback.call(this, dataURL);
    canvas = null; 
  };
  img.src = url;
}
```
## 调用：
```
let url = "https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"
this.convertImgToBase64(url,(base64Img)=>{
  console.log(base64Img)//转化后的base64文件
})
```
