---
published: true
layout: post
date: '2021-03-31 18:10:20 +0300'
tags:
  - Vue
---
## A New Post

```
npm i swiper@5.4.5 vue-awesome-swiper@3 -S
```

main.js
```
import VueAwesomeSwiper from 'vue-awesome-swiper'
import '../styles/swiper.min.css'
Vue.use(VueAwesomeSwiper, /* { default global options } */)

new Vue({
  el: "#app",
  render: h => h(App),
})
```

组件内
