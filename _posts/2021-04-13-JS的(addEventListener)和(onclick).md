---
published: true
---
## JS事件绑定(addEventListener)和普通事件(onclick)有什么区别

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
- addEventListener对任何DOM都是有效的，而onclick仅限于HTML
- addEventListener可以控制listener的触发阶段,（捕获/冒泡）。对于多个相同的事件处理器，不会重复触发，不需要手动使用removeEventListener清除;
- IE9使用attachEvent和detachEvent;
