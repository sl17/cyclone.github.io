---
published: true
layout: post
date: '2024-08-27 16:45:45 +0300'
tags:
  - Vue3
---
### vue3使用emit和update


#### vue3使用emit和update:modelValue

### 父组件

```
<template>
  <Test v-model="ruleForm"></Test>
  <button @click="logD">0000</button>
</template>
<script setup lang="ts">
import Test from './components/Test.vue'
const ruleForm = ref({
  institution: '',
  event_name: '',
  event_date: ''
})
const logD = () => {
  console.log(ruleForm.value)
}
</script>
```
### 子组件

```
<template>
  <div class="">
    <el-select v-model="data.institution">
      <el-option
        v-for="item in [
          { label: 'asdd', value: 1 },
          { label: 'aqwesdd', value: 2 }
        ]"
        :key="item.value"
        :label="item.label"
        :value="item.value"
      />
    </el-select>
    <el-input v-model="data.event_name" :rows="2" type="textarea"/>
    <el-date-picker v-model="data.event_date" type="date" format="YYYY.MM.DD" value-format="YYYY-MM-DD"/>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
const props = defineProps(['modelValue'])
const emit = defineEmits(['update:modelValue'])
const data = computed({
  get () {
    return props.modelValue
  },
  set (val) {
    emit('update:modelValue', val)
  }
})
</script>
<style lang="scss" scoped></style>

```
