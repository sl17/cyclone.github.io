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
import Vue from "vue";

import VueAwesomeSwiper from 'vue-awesome-swiper'
import '../styles/swiper.min.css'
Vue.use(VueAwesomeSwiper)

new Vue({
  el: "#app",
  render: h => h(App),
})
```

组件内

导入
```
import "../../styles/swiper.min.css";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";

```

```
components: {
  Swiper,
  SwiperSlide,
},
```
