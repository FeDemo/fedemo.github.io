---
layout:     post
title:      redis安装使用笔记
subtitle:   hello redis
date:       2018-05-31
author:     Fe
header-img: img/post-bg-geometry.jpg
keywords_post:  "redis，redis安装使用笔记,redis在linux上的安装,redis在windows上的安装"
catalog: true
tags:
    - redis
---

## redis的安装

#### Windows

>下载地址: [https://github.com/MSOpenTech/redis/releases](https://github.com/MSOpenTech/redis/releases)


![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-05-31-hello-redis/1.png)

>安装

下载后解压到本地

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-05-31-hello-redis/2.png)

>开启服务

redis在windows上可以直接使用,不需要安装   

使用cmd命令启动服务
```
> d:
> cd redis
> redis-server.exe redis.windows.conf
```

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-05-31-hello-redis/3.png)

>连接测试

使用redis客户端连接时,redis服务记得不要关

使用cmd启动客户端
```
> d:
> cd redis
> redis-cli.exe -h 127.0.0.1 -p 6379
```

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-05-31-hello-redis/4.png)

#### linux

>下载地址: [http://redis.io/download](http://redis.io/download)

下载并解压redis
```
> wget http://download.redis.io/releases/redis-2.8.17.tar.gz
> tar xzf redis-2.8.17.tar.gz
> cd redis-2.8.17
> make
```

>启动服务

在redis的安装目录,开启服务
```
> src/redis-server
```

带配置的服务
```
> src/redis-server redis.conf
```

>客户端连接

```
> src/redis-cli
```

>关闭服务

```
src/redis-cli shutdown
```

## 配置密码

目前连接redis都是不需要密码的,可以通过修改`redis.windows.conf`设置密码(linux修改`redis.conf`文件)

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-05-31-hello-redis/5.png)

找到requirepass,取消`#`注释 再后面设置密码,
```
requirepass test
```

这样下次启动时就需要使用密码连接

#### 使用密码连接

>windows  

```
redis-cli.exe -h 123.123.123.123 -p 6379 -a test
```
>linux   

```
src/redis-cli -a test
```

## 连接远程redis服务

```
> redis-cli.exe -h 123.123.123.123 -p 6379 -a test
```
和连接本地一样,只要输入远程redis服务的ip和端口号就好了




<br>
