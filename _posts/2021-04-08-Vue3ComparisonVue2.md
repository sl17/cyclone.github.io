---
published: true
layout: post
date: '2021-04-08 13:32:20 +0300'
tags:
  - Vue3
---
## 简单介绍vue2和vue3的对比变化


<details>
  <summary>生命周期函数1</summary>
  <div class="details-box">
    萨达撒所萨达按时萨达萨达啊
	<xmp>
    <div>is div</div>
   </xmp>
  </div>
</details>

<details>
  <summary>插槽</summary>
  <div class="details-box">
    默认插槽 v2
	<xmp>
    //父组件
    <div>装一杯牛奶</div>
    //item子组件
    <slot></slot>
   </xmp>
    
    默认插槽 v3
    原来的solt属性可以定义在任何元素上，现在v-solt只能是template元素上
	<xmp>
    //父组件
    // v-slot:default可以不加,只能定义在template上
    <template v-slot:default> 
      <div>装一杯牛奶</div>
    </template>
    //item子组件
    <slot></slot>
   </xmp>
    
   作用域插槽 v2
   <xmp>
    //父组件
    <div solt="size" slot-scope="data">
      {{data.msg}}
    </div>
    //item子组件
    <slot name="size" :msg="msg"></slot>
   </xmp>
    
   作用域插槽 v3
   <xmp>
    //父组件
    <template v-slot:default="data"> //具名写法
      <div>
        {{data.msg}}   
      </div>
    </template>
     or
    <template v-slot="data">
     <div > {{data.msg}} </div>
    </template>	
    //item子组件
    <slot name="size" :msg="msg"></slot >
   </xmp>
   当为独占默认插槽时，v-solt可以省略default不写
	注意默认插槽的缩写语法不能和具名插槽混用，因为它会导致作用域不明确下面是官方的例子
    
  </div>
</details>
