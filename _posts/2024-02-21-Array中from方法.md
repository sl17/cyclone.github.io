---
published: true
layout: post
date: '2024-02-21 08:21:20 +0300'
tags:
  - JS
---
## Array中from方法


### JS中 Array.from 函数的使用

```
// 使用箭头函数作为映射函数去操作多个元素
Array.from([1, 2, 3], (x) => x + x);
// [2, 4, 6]

// 生成一个数字序列。因为数组在每个位置都使用 `undefined` 初始化，下面的 `v` 值将是 `undefined`
Array.from({ length: 5 }, (v, i) => i);
// [0, 1, 2, 3, 4]

```

乱序
```
// 生成一个包含1到100的数组  
let array = Array.from({ length: 100 }, (_, i) => i + 1);

// 使用sort方法和一个随机比较函数来乱序数组  
array.sort(() => Math.random() - 0.5);

// 打印乱序后的数组  
console.log(array);
```
