---
published: true
layout: post
date: '2017-03-25 13:32:20 +0300'
tags:
  - JavaScript
---
### 让ie浏览器兼容input的placeholder属性


```
style：
.phcolor{color: #999}/*自定义颜色样式*/

script：

$(function(){
  //判断浏览器是否支持placeholder属性
  supportPlaceholder='placeholder'in document.createElement('input'),
  placeholder=function(input){
    var text = input.attr('placeholder'),
    defaultValue = input.defaultValue;
    if(!defaultValue){
      input.val(text).addClass("phcolor");
    }
    input.focus(function(){
      if(input.val() == text){
        $(this).val("");
      }
    });
    input.blur(function(){
      if(input.val() == ""){
        $(this).val(text).addClass("phcolor");
      }
    });
    //输入的字符不为灰色
     input.keydown(function(){
       $(this).removeClass("phcolor");
     });
   };
   //当浏览器不支持placeholder属性时，调用placeholder函数
   if(!supportPlaceholder){
     $('input').each(function(){
       text = $(this).attr("placeholder");
       if($(this).attr("type") == "text"){
         placeholder($(this));
       }
     });
   }
 });
 ```
 以上
