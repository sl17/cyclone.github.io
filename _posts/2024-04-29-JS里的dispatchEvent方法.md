---
published: true
layout: post
date: '2024-04-29 13:55:45 +0300'
tags:
  - JS
---
### JS里的dispatchEvent方法


#### JS里的dispatchEvent方法会向一个指定的事件目标派发一个 Event，并以合适的顺序（同步地）调用所有受影响的 EventListener



```
<button class="btn">测试dispatchEvent()方法</button>
<div onclick="clickFn()">点击</div>
<script>
    let btn = document.querySelector('.btn');

    btn.addEventListener('click', function () {
        console.log('点击了 button');
    });

    function clickFn() {
        console.log('点击了  div');
        let clickEvent = new Event('click');
        btn.dispatchEvent(clickEvent);
        // 同上
        // let clickMouseEvent = new MouseEvent('click');
        // btn.dispatchEvent(clickMouseEvent);
    }
    let clickMouseEvent = new MouseEvent('click');
    btn.dispatchEvent(clickMouseEvent);
</script>

```

`vue 的情况`
```
this.$refs.inputer.dispatchEvent(new MouseEvent('click'))
```


