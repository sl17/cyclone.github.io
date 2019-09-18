---
published: true
layout: post
date: '2018-04-17 13:32:20 +0300'
tags:
  - 软件安装
---
## Windows下安装Mongodb及配置

先在官网下载安装包
[mongodb下载](https://www.mongodb.com/download-center/community)

### 第一步
![第一步]({{site.baseurl}}/assets/img/demo/201909/2019-09-17_0001.png)

### 第二步
![第二步]({{site.baseurl}}/assets/img/demo/201909/2019-09-17_0002.png)

### 第三步
![第三步]({{site.baseurl}}/assets/img/demo/201909/2019-09-17_0003.png)

### 第四步
![第四步]({{site.baseurl}}/assets/img/demo/201909/2019-09-17_0004.png)

### 第五步
![第五步]({{site.baseurl}}/assets/img/demo/201909/2019-09-17_0005.png)

### 第六步
![第六步]({{site.baseurl}}/assets/img/demo/201909/2019-09-17_0006.png)

### 第七步
![第七步]({{site.baseurl}}/assets/img/demo/201909/2019-09-17_0007.png)

### 第八步
![第八步]({{site.baseurl}}/assets/img/demo/201909/2019-09-17_0008.png)

在安装路径下新建文件夹
- data
 - db
- log

新建文件
mongo.conf

记事本打开mongo.conf文件 配置一下

```
#数据库路径  
dbpath=G:\mongodb\data\db
#日志输出文件路径  
logpath=G:\mongodb\log\mongo.log
#错误日志采用追加模式  
logappend=true  
#启用日志文件，默认启用  
journal=true  
#这个选项可以过滤掉一些无用的日志信息，若需要调试使用请设置为false  
quiet=true  
#端口号 默认为27017  
port=27017
```
### 启动MongoDB服务(打开第一个CMD窗口)

- 打开cmd命令行
- 进入`G:\mongodb\bin`目录
- 输入如下的命
令启动mongodb服务：`mongod --dbpath G:\mongodb\data\db`

### 配置环境变量

![第八步]({{site.baseurl}}/assets/img/demo/201909/2019-09-18_0001.png)

### 配置window 服务（打开第二个CMD窗口）
以管理员身份运行cmd
进入mongodb安装目录下的bin目录
输入`mongod --dbpath "G:\mongodb\data\db" --logpath "G:\mongodb\log\mongo.log" --install --serviceName "MongoDB"`
再输入`net start mongodb`
出现
```
MongoDB 服务正在启动
MongoDB 服务无法启动

发生服务特定错误： 100.
请键入 NET HELPMSG 3547 以获得更多的帮助。
```
> 关闭第一个cmd窗口

再输入`net start mongodb`
出现
```
MongoDB 服务正在启动
MongoDB 服务已经启动成功
```