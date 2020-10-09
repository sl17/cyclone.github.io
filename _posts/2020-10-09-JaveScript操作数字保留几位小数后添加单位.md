---
published: false
---
## JaveScript操作数字保留几位小数后添加单位

```
function unit(num, digits) {
  let arr = [
    { name: "k", num: 1000 },
    { name: "w", num: 10000 },
    { name: "亿", num: 100000000 }
  ];
  let str = "";
  arr.map(e => {
    if (Math.floor(Math.abs(num / e.num)) > 0) {
      str = (num / e.num).toFixed(digits) * 1 + e.name;
    }
    if (Math.abs(num / 1000) < 1) {
      str = num;
    }
  });
  return str;
}
    
```
