---
published: true
layout: post
date: '2021-04-13 13:32:20 +0300'
tags:
  - JavaScript
---
## JS事件绑定(addEventListener)和普通事件(onclick)有什么区别,扩展jq中的on()和click()区别；

### 普通事件（onclick）
- 普通事件就是直接触发事件，同一时间只能指向唯一对象，所以会被覆盖掉。

- 解绑
```
window.onresize = function(event){
    event.preventDefault();
    console.log('调整浏览器窗口大小时触发resize事件');
}
window.onresize = none;
```

### 事件绑定（addEventListener）

- 事件绑定就是对于一个可以绑定的事件对象，进行多次绑定事件都能运行。
- `addEventListener`对任何DOM都是有效的，而`onclick`仅限于HTML
- addEventListener可以控制`listener`的触发阶段,（捕获/冒泡）。对于多个相同的事件处理器，不会重复触发，不需要手动使用`removeEventListener`清除;
- IE9使用`attachEvent`和`detachEvent`;

- 解绑
```
function resizeWindow(event){
  event.preventDefault();
  console.log('调整浏览器窗口大小时触发resize事件')
}
window.addEventListener('resize', resizeWindow, false);
window.removeEventListener('resize', resizeWindow, false);
```

## 扩展
JQ中的on()和click()区别

- `click()`属于静态加载，当页面加载完，就不在为新增加的元素添加点击事件。

- `on()`属于动态加载，当页面加载完，可以为新增加的元素添加事件。但是必须选定负级元素。