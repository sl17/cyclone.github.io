---
published: true
layout: post
date: '2019-10-29 13:32:20 +0300'
tags:
  - Vue
---
## Vue项目Iview中tabs获取子元素id传值

`TabPane`上的`name`属性会自动通过父组件上的方法传到方法里面
```
<template>
  <Tabs type="card" @on-click="getItem">
    <TabPane v-for="tab in tabs" :name='tab.id' :key="tab.id" :label="tab.nickname"></TabPane>
  </Tabs>
</template>
<script>
  export default {
    data(){
      return{
        tabs: [
          {
            id: "111111",
            nickname: "Bob"
          },
          {
            id: "222222",
            nickname: "Dear"
          },
          {
            id: "333333",
            nickname: "Job"
          }
        ],
      }
    },
    methods: {
      getItem(index) {
        console.log(index) //111111,222222,333333
      }
    }
  }
</script>
```
