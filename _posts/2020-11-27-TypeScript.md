---
published: false
layout: post
date: '2020-11-27 23:32:20 +0300'
tags:
  - TypeScript
---
### 基础类型
	let isDon :boolean = false;
	let str :string = "Hello TS";
	let num :number = 123;

### 函数类型注解
	//函数没有返回值
	function sayHello() : void {
		console.log("hello");
	}
	//函数参数是number类型，返回值是number类型
	function getTotal(one: number, two: number) : number{
		return one + two;
	}
	//函数传参是对象的话，这样定义类型
	function add({one, two}:{one: number, two: number}): number{
		return one + two;
	}
	//表示这个方法永远执行不完
	function forNever() : never {
		while( true ){
			console.log('print')
		}
	}
	//可选参数
	function run3(name :string, age? :number) : string{
    	if(age){
    		return `我是${name},今年${age}岁.`
    	}else{
    		return `我是${name},年龄保密.`
    	}
    }
	//剩余参数
	function sunf(...d :number[]) :number{
    	let s: number = 0;
    	for(let i:number = 0;i &lt; d.length; i++){
    		s += d[i]
    	}
    	return s
    }

### 数组类型注解
    const numberArr : number[] = [1, 2, 3];
    const stringArr : string[] = ['1', '2', '3'];
    const arr : (number | string)[] = [1, '3', 2];
	//type alias 类别名
	type Lady = {name: string, age: number};
	//类的形式
	class Madam {
		name: string;
		age: number;
	}
	const girls: Lady[] = [
		{name:'Lux', age: 18},
		{name:'Rax', age: 28},
	]
	const girls2: Madam[] = [
		{name:'Lux', age: 18},
		{name:'Rax', age: 28},
	]
