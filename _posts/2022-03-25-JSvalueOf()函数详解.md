---
published: true
layout: post
date: '2022-03-25 10:27:20 +0300'
tags:
  - JavaScript
---
## JavaScript valueOf() 函数详解




```
// Array：返回数组对象本身
var array = ["CodePlayer", true, 12, -5];
document.writeln( array.valueOf() === array ); // true

// Date：当前时间距1970年1月1日午夜的毫秒数
var date = new Date(2013, 7, 18, 23, 11, 59, 230);
document.writeln( date.valueOf() ); // 1376838719230

// Number：返回数字值
var num = 15.26540;
document.writeln( num.valueOf() ); // 15.2654

// 布尔：返回布尔值true或false
var bool = true;
document.writeln( bool.valueOf() === bool ); // true
// new一个Boolean对象
var newBool = new Boolean(true);
// valueOf()返回的是true，两者的值相等
document.writeln( newBool.valueOf() == newBool ); // true
// 但是不全等，两者类型不相等，前者是boolean类型，后者是object类型
document.writeln( newBool.valueOf() === newBool ); // false

// Function：返回函数本身
function foo(){ 
}
document.writeln( foo.valueOf() === foo ); // true
var foo2 = new Function("x", "y", "return x + y;");
document.writeln( foo2.valueOf() === foo2 ); // true

// Object：返回对象本身
var obj = {name: "张三", age: 18};
document.writeln( obj.valueOf() === obj ); // true

// String：返回字符串值
var str = "http://www.365mini.com";
document.writeln( str.valueOf() === str ); // true
// new一个字符串对象
var str2 = new String("http://www.365mini.com");
// 两者的值相等，但不全等，因为类型不同，前者为string类型，后者为object类型
document.writeln( str2.valueOf() === str2 ); // false"
```
