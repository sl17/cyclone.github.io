---
published: true
layout: post
date: '2023-06-06 12:45:09 +0800'
tags:
  - ElementUI
---
## ElementUI的table筛选


#### ElementUI的table筛选

```
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 引入样式 -->
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
    <script src="./vue@2.6.14.js"></script>
    <!-- 引入组件库 -->
    <script src="https://unpkg.com/element-ui/lib/index.js"></script>
    <style>
       
        .trim-size-call i{
            position: relative;
            display: inline-block;
            top: 4px;
            height: 14px;
            width: 20px;
        }
        .trim-size-call i::after{
            content: "";
            position: absolute;
            top: 7px;
            left: 8px;
            display: inline-block;
            border-top: 1px solid #f7f7f9;
            width: 6px;
            height: 5px;
            background-color: #7d7d80;
            border-radius: 1px;
        }
        .trim-size-call i::before{
            position: absolute;
            border-radius: 5px;
            top: -3px;
            left: 1px;
            content: "";
            border-top: 13px solid #7d7d80;
            border-left: 10px solid transparent;
            border-right: 11px solid transparent;
        }
    </style>
</head>

<body>
    <div id="app">
        <template>
            <el-table :data="tableData" height="250" border style="width: 100%" @filter-change="filterHandler">
                <el-table-column label="日期" width="180"
                    column-key="status"
                    :label-class-name="'trim-size-call'"
                    :filters="[
                        {text: '2016-05-01', value: '2016-05-01'}, 
                        {text: '2016-05-02', value: '2016-05-02'}, 
                        {text: '2016-05-03', value: '2016-05-03'}, 
                        {text: '2016-05-04', value: '2016-05-04'}
                    ]"
                >
                    <template slot-scope="scope">
                        {{ scope.row.date  ||'-'}}
                    </template>
                </el-table-column>
                <el-table-column prop="name" label="姓名" width="180">
                </el-table-column>
                <el-table-column prop="address" label="地址">
                </el-table-column>
            </el-table>
        </template>
    </div>
    <div id="mount-point"></div>
    <script>
        new Vue({
            el: '#app',
            data: function () {
                return {
                    tableData: [{
                        date: '2016-05-03',
                        name: '王小虎',
                        address: '上海市普陀区金沙江路 1518 弄'
                    }, {
                        date: '2016-05-02',
                        name: '王小虎',
                        address: '上海市普陀区金沙江路 1518 弄'
                    }, {
                        date: '2016-05-04',
                        name: '王小虎',
                        address: '上海市普陀区金沙江路 1518 弄'
                    }, {
                        date: '2016-05-01',
                        name: '王小虎',
                        address: '上海市普陀区金沙江路 1518 弄'
                    }, {
                        date: '2016-05-08',
                        name: '王小虎',
                        address: '上海市普陀区金沙江路 1518 弄'
                    }, {
                        date: '2016-05-06',
                        name: '王小虎',
                        address: '上海市普陀区金沙江路 1518 弄'
                    }, {
                        date: '2016-05-07',
                        name: '王小虎',
                        address: '上海市普陀区金沙江路 1518 弄'
                    }]
                }
            },
            directives: {
                outsild: {
                    inserted(el) {
                        document.addEventListener('click', function (event) {
                            if (!(el.contains(event.target))) {
                                el.style.display = 'none'
                            }
                        })
                    },
                },

            },
            mounted() {
                let that = this;
                document.addEventListener('click', function (event) {
                    const div = that.$refs.showBox;
                    if (div) {
                        that.isShow = true
                        if (!(div.contains(event.target))) {
                            that.isShow = false
                        }
                    }
                })
            },
            computed: {

            },
            created() {

            },
            methods: {
                filterHandler(value, row, column) {
                    console.log( value);
                   
                },
            }
        })

    </script>
</body>

</html>

```

