---
published: true
layout: post
date: '2017-04-21 13:32:20 +0300'
tags:
  - 其他
---
## cookie和session和sessionStorage和localStore区别

cookie、session区别

- cookie 存储于浏览器端，而 session 存储于服务端
- cookie 存储容量有限制，单个cookie 保存数据不能超过4k，且很多浏览器限制一个站点最多保存20个cookie。而对于 session ，其默认大小一般是1024k


cookie、sessionStorage和localStore区别
- localStorage和sessionStorage：可以保存5MB的信息。
- cookie在浏览器和服务器间来回传递， sessionStorage和localStorage不会。
- sessionStorage和localStorage的存储空间更大。
- sessionStorage和localStorage有更多丰富易用的接口。
- sessionStorage和localStorage各自独立的存储空间。
- sessionStorage和localStorage仅在客户端（即浏览器）中保存，不参与和服务器的通信

以上
