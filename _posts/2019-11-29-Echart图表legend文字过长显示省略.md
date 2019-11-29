---
published: true
layout: post
date: '2019-11-29 13:32:20 +0300'
tags:
  - Echarts
---
## Echart图表legend文字过长显示省略，鼠标移入显示全部

```
app.title = '环形图';

option = {
  tooltip: {
    trigger: 'item',
    formatter: "{a} <br/>{b}: {c} ({d}%)"
  },
  legend: {
    orient: 'vertical',
    x: 'left',
    formatter: function (name) {
      if (!name) return '';
      if (name.length > 5) {
        name = name.slice(0, 5) + '...';
      }
    },
  },
  series: [
    {
      name: '访问来源',
      type: 'pie',
      radius: ['50%', '70%'],
      avoidLabelOverlap: false,
      label: {
        normal: {
          show: false,
          position: 'center'
        },
        emphasis: {
          show: true,
          textStyle: {
            fontSize: '30',
            fontWeight: 'bold'
          }
        }
      },
      labelLine: {
        normal: {
          show: false
        }
      },
      data: [
        { value: 335, name: '直接访问' },
        { value: 310, name: '邮件营销' },
        { value: 234, name: '联盟广告' },
        { value: 135, name: '视频广告' },
        { value: 1548, name: '搜索引擎' }
      ]
    }
  ]
};
```

![扫码]({{site.baseurl}}/assets/img/demo/201911/2019-11-29_00001.png)
