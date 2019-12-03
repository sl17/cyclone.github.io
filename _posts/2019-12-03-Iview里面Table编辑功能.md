---
published: true
layout: post
date: '2019-12-03 13:32:20 +0300'
tags:
  - Iview
---
## A New Post

```
<template>
  <Table border :columns="columns1" :data="data1"></Table>
</template>
<script>
export default {
  data() {
    return {
      columns1: [
        {
          title: "Name",
          key: "name"
        },
        {
          title: "Age",
          key: "age",
          render: (h, params) => {
            if (params.row.$isEdit) {
              return h("input", {
                domProps: {
                  value: params.row.age
                },
                on: {
                  input: function(event) {
                    params.row.age = event.target.value;
                  }
                }
              });
            } else {
              return h("div", params.row.age);
            }
          }
        },
        {
          title: "Address",
          render: (h, params) => {
            return h(
              "Button",
              {
                props: {
                  type: "text",
                  size: "small"
                },
                on: {
                  click: () => {
                    if (params.row.$isEdit) {
                      this.handleSave(params.row);
                    } else {
                      this.handleEdit(params.row);
                    }
                  }
                }
              },
              params.row.$isEdit ? "保存" : "编辑"
            );
          }
        }
      ],
      data1: [
        {
          name: "John Brown",
          age: 18,
          address: "New York No. 1 Lake Park",
          date: "2016-10-03"
        },
        {
          name: "Jim Green",
          age: 24,
          address: "London No. 1 Lake Park",
          date: "2016-10-01"
        },
        {
          name: "Joe Black",
          age: 30,
          address: "Sydney No. 1 Lake Park",
          date: "2016-10-02"
        },
        {
          name: "Jon Snow",
          age: 26,
          address: "Ottawa No. 2 Lake Park",
          date: "2016-10-04"
        }
      ]
    };
  },
  methods: {
    handleEdit(row) {
      this.$set(row, "$isEdit", true);
    },
    handleSave(row) {
      this.$set(row, "$isEdit", false);
    }
  }
};
</script>

```

![可编辑]({{site.baseurl}}/assets/img/demo/201912/2019-12-03_00001.png)
