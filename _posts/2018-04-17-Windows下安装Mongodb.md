---
published: true
layout: post
date: '2018-04-17 13:32:20 +0300'
tags:
  - 软件安装
---
## Windows下安装Mongodb及配置

### 第一步
![第一步](2019-09-17_0001.png)

### 第二步
![第二步](2019-09-17_0002.png)

### 第三步
![第三步](2019-09-17_0003.png)

### 第四步
![第四步](2019-09-17_0004.png)

### 第五步
![第五步](2019-09-17_0005.png)

### 第六步
![第六步](2019-09-17_0006.png)

### 第七步
![第七步](2019-09-17_0006.png)

在安装路劲下新建文件夹
- data
 - db
- log

新建文件
mongo.conf

记事本打开mongo.conf文件 配置一下

```
#数据库路径  
dbpath=C:\mongodb\data\db
#日志输出文件路径  
logpath=C:\mongodb\log\mongo.log
#错误日志采用追加模式  
logappend=true  
#启用日志文件，默认启用  
journal=true  
#这个选项可以过滤掉一些无用的日志信息，若需要调试使用请设置为false  
quiet=true  
#端口号 默认为27017  
port=27017
```
### 启动MongoDB服务

- 打开cmd命令行
- 进入G:\mongodb\bin目录
- 输入如下的命
令启动mongodb服务：mongod --dbpath G:\mongodb\data\db









