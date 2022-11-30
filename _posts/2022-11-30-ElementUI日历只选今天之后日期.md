---
published: true
layout: post
date: '2022-11-30 14:12:20 +0300'
tags:
  - 页面布局
---
## ElementUI 日历只选今天之后日期


#### ElementUI日历组件限制只能选今天之后的日期
```
<el-date-picker 
	:picker-options="pickerOptions" 
	value-format="yyyy-MM-dd">
</el-date-picker>


```
```
data() {
	return {
		'pickerOptions':{
            disabledDate(time) {
                if(location.origin=='http://dev.ng-test.linkedprint.cn'){
                }else{
                    return time.getTime() < Date.now()-8.64e7;
                }
            }
        },
	}
}

```
