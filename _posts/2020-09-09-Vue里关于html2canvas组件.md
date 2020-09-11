---
published: true
layout: post
date: '2020-09-09 18:36:20 +0300'
tags:
  - Vue
---
## Vue里关于html2canvas组件
## 安装
```
npm install html2canvas
```
```
import html2canvas from 'html2canvas'
```

`useCORS:true,//（图片跨域相关）`
`allowTaint:false,//允许跨域（图片跨域相关）`

## 用法

### 基础用法
```
html2canvas(document.body).then(function(canvas) {
  document.body.appnedChild(canvas)
})
```
### 基础用法2
```
setTimeout(() => {
  this.keepImage();
}, 300);
base64ToBlob(urlData) {
  var arr = urlData.split(",");
  var mime = arr[0].match(/:(.*?);/)[1] || "image/png";
  var bytes = window.atob(arr[1]);
  var ab = new ArrayBuffer(bytes.length);
  var ia = new Uint8Array(ab);
  for (var i = 0; i < bytes.length; i++) {
    ia[i] = bytes.charCodeAt(i);
  }
  return new Blob([ab], {
    type: mime,
  });
},
keepImage() {
  html2canvas(this.$refs.shareBoxBig, { scale: 2.1, useCORS: true }).then(
    (canvas) => {
      let imgUrl = canvas.toDataURL("image/png");
      let tmpBlob = this.base64ToBlob(imgUrl);
      this.shareImg = window.URL.createObjectURL(tmpBlob);
      this.loadingBox = true;
    }
  );
},
```
### 基础用法3
```
keepImage2() {
  const self = this;
  [3, 4].forEach((i) => {
    html2canvas(self.$refs[`pictorialDom${i}`], {
      useCORS: true,
    }).then((canvas) => {
      let imgUrl = canvas.toDataURL("image/png");
      let tmpBlob = self.base64ToBlob(imgUrl);
      self.downloadDate[`pageDateImg${i}`] = window.URL.createObjectURL(
        tmpBlob
      );
      this.loadingBox = false;
    });
  });
},
```



## 配置项
| 属性名 | 默认值 | 描述 |
| :-----| :---- | :---- |
| allowTaint |	false	| 是否允许不同源的图片污染画布 |
| backgroudColor | #ffffff | 画布背景颜色，如果 DOM 中没有指定，则默认为白色。设置 null 则为透明 |
| canvas | null | 现有的 canvas 元素，用作绘图的基础 |
| foreignObjectRendering| false | 如果浏览器支持 ForeignObject rendering，是否使用它 |
| imageTimeout | 15000 | 加载图片超时（毫秒）。设置 0 关闭超时 |
| ignoreElements |	(element) => false|	布尔函数，用于从渲染中删除匹配元素。|
| logging |	true |启用日志记录以进行调试 |
| onclone |	null | 在克隆文档流进行渲染时调用的回调函数，可用于修改将在不影响原始源文档流的情况下呈现的内容 |
| proxy	| null | Url 到代理，用于加载跨域图片资源。如果留空，则不会加载跨域图片。|
| removeContainer | true | 是否清理克隆的 DOM 元素，html2canvas 暂时创建。|
| scale | window.devicePixelRatio |	用于渲染的比例，默认为浏览器设备像素比率。|
| useCORS | false |	是否尝试使用 CORS 从服务器加载图片 |
| width | Element width | canvas 画布宽度 |
| height | Element height | canvas 画布高度 |
| x | Element x-offset | 裁剪画布 x 坐标 |
| y | Element y-offset | 裁剪画布 y 坐标 |
| scrollX	Element | scrollX | 渲染元素时使用的 X 滚动位置（比如元素使用 position: fixed）|
| scrollY	Element | scrollY |	渲染元素时使用的 Y 滚动位置（比如元素使用 position: fixed）|
| windowWidth |	Window.innerWidth |	渲染 Element 时要使用的窗口宽度，这可能会影响媒体查询等内容 |
| windowHeight | Window.innerHeight |	渲染 Element 时要使用的窗口高度，这可能会影响媒体查询等内容 |



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

## 不支持的 CSS 属性

### 这些 CSS 属性当前版本还不支持

- background-blend-mode
- border-image
- box-decoration-break
- box-shadow
- filter
- font-variant-ligatures
- mix-blend-mode
- object-fit
- repeating-linear-gradient()
- writing-mode
- zoom
