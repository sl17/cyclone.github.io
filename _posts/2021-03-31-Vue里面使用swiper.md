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
      },
      options: {
        verticalCentered: true, //定义每一页的内容是否垂直居中
        afterLoad: this.afterLoad, //滚动到某一屏后的回调函数
        autoScrolling: true,
        navigation: true,
        sectionsColor: [
          "#41b883",
          "#ff5f45",
          "#0798ec",
          "#fec401",
          "#1bcee6",
          "#ee1a59",
          "#2c3e4f",
          "#ba5be9",
          "#b4b8ab",
        ],
      },
    };
  },
  created() {
    vm = this;
  },
  mounted() {
  },
  computed: {
    swiper() {
      return this.$refs.mySwiper.$swiper;
    },
  },
  methods: {
    // afterLoad: function (origin, destination, direction) {
    //   console.log(destination.index);
    // },
    // gotolastpage(obj) {
    //   fullpage_api.moveTo(obj, 0);
    // },
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
