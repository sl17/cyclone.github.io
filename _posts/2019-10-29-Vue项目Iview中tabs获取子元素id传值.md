---
published: false
---
## Vue项目Iview中tabs获取子元素id传值

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
