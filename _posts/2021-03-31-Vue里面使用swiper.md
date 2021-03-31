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
swiper.min.css 文件下载到项目里 放在styles文件夹下

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

html
```
<div class="swiper-container">
  <swiper ref="mySwiper" :options="swiperOptions">
    <swiper-slide> slide1 <button @click="tabPage(3)">ch</button></swiper-slide>
    <swiper-slide> slide2 </swiper-slide>
    <swiper-slide> slide3 </swiper-slide>
    <swiper-slide> slide4  <button @click="tabPage(0)">ch</button></swiper-slide>
  </swiper>
</div>

```
导入
```
import "../../styles/swiper.min.css";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
let vm = null;
export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      pageIndex: 0,
      changePage: 0,
      swiperOptions: {
        pagination: {
          el: ".swiper-pagination",
        },
        mousewheel: true,
        direction: "vertical",
        speed: 1000,
        on: {
          slideChange: function () {
            vm.pageIndex = this.activeIndex;
          },
        },
      }
    };
  },
  created() {
    vm = this;
  },
  computed: {
    swiper() {
      return this.$refs.mySwiper.$swiper;
    },
  },
  methods: {
    tabPage(index) {
      // this.$refs.mySwiper.$swiper.slideTo(index, 1000, false)
      // console.log(this.$refs.mySwiper.$swiper)
      this.swiper.slideTo(index, 1000, false);
    },
  },
  watch: {
    pageIndex(v, o) {
      console.log(v, o);
    },
  },
};
```
