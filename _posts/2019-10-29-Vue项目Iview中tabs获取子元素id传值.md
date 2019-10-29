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
  {
    data() {
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
    }
  }
</script>
```