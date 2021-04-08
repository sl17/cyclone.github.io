---
published: true
layout: post
date: '2021-04-08 13:32:20 +0300'
tags:
  - Vue3
---
## 简单介绍vue2和vue3的对比变化


<details>
  <summary>生命周期函数</summary>
  <div class="details-box">
    <p><s>beforeCreate</s> -> use setup()</p>
    <p><s>created</s> -> use setup()</p>
    <p>beforeMount -> onBeforeMount</p>
    <p>mounted -> onMounted</p>
    <p>beforeUpdate -> onBeforeUpdate</p>
    <p>updated -> onUpdated</p>
    <p>beforeDestroy -> onBeforeUnmount</p>
    <p>destroyed -> onUnmounted</p>
    <p>errorCaptured -> onErrorCaptured</p>
  </div>
</details>

<details>
  <summary>插槽</summary>
  <div class="details-box">
    v2 默认插槽
    <xmp>
      //父组件
      <div>装一杯牛奶</div>
      //item子组件
      <slot></slot>
    </xmp>

    v3 默认插槽
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

    v2 作用域插槽 v2
    <xmp>
      //父组件
      <div solt="size" slot-scope="data">data.msg</div>
      //item子组件
      <slot name="size" :msg="msg"></slot>
    </xmp>

    v3 作用域插槽
    <xmp>
      //父组件
      <template v-slot:default="data"> //具名写法
        <div>{data.msg}</div>
      </template>
      or
      <template v-slot="data">
        <div> {data.msg} </div>
      </template>
      //item子组件
      <slot name="size" :msg="msg"></slot>
    </xmp>
    当为独占默认插槽时，v-solt可以省略default不写；
    注意默认插槽的缩写语法不能和具名插槽混用，因为它会导致作用域不明确下面是官方的例子
    
    无效，会导致警告
    <xmp>
      <current-user v-slot="slotProps">
        <template v-slot:other="otherSlotProps">
          slotProps is NOT available here
        </template>
      </current-user>
    </xmp>

    v3 解构写法
    <xmp>
      <template v-slot:default="{msg}"> //解构
        <div>{msg}</div>
      </template>
    </xmp>
    v-slot 的解构还提供 重命名的写法
    <xmp>
      <template v-slot:default="{ msg : size }"> //解构
        <div>{size}</div>
      </template>
    </xmp>
    插槽的缩写
    可以把参数之前的所有内容 (v-slot:) 替换为字符 #。例如 v-slot:header 可以被重写为 #header
    v-slot:后面必须有值，不可写成#="{data}"
  </div>
</details>

<details>
  <summary>过滤器</summary>
  <div class="details-box">
  	从 Vue 3.0 开始，过滤器已删除，不再支持。
  </div>
</details>

<details>
  <summary>其他</summary>
  <div class="details-box">
    <p>Vue 3 的 Template 支持多个根标签，Vue 2 不支持</p>
    <p>Vue 3 有 createApp()，而 Vue 2 的是 new Vue()</p>
   
  </div>
</details>

<details>
  <summary>setup</summary>
  <div class="details-box">
    <p>执行时机</p>
     setup 函数会在 beforeCreate 之后、created 之前执行
    <p>接收传参数据</p>
     1、props
    <pre><code>
    	export default {
        props: {
          msg: {
            type: String,
            default: () => {}
          }
        },
        setup(props) {
          console.log(props);
        }
      }
    </code></pre>
    
    2、context
    
    setup 函数的第二个形参是一个上下文对象，这个上下文对象中包含了一些有用的属性，这些属性在 vue 2.x 中需要通过 this 访问到，在 vue 3.x 中，它们的访问方式如下：
    <pre><code>
    	const MyComponent = {
        setup(props, context) {
          context.attrs
          context.slots
          context.parent
          context.root
          context.emit
          context.refs
        }
      }
    </code></pre>
  </div>
</details>
