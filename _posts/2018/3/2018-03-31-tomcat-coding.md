---
layout:     post
title:      tomcat笔记,编码问题
subtitle:   tomcat coding
date:       2018-03-31
author:     Fe
header-img: img/home-bg-o.jpg
keywords_post:  "tomcat,tomcat默认编码,修改tomcat默认编码,javaweb,javaweb项目乱码"
catalog: true
tags:
    - tomcat
    - Java
---
>tomcat笔记   
>javaweb项目乱码解决方案

## tomcat默认编码

tomcat7及之前版本默认编码格式为`iso8859-1`   

tomcat8以后默认编码格式是`utf-8`

## 修改tomcat配置文件

在`%tomcat%\conf\server.xml`中找到
```xml
<Connector port="8080" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />
```

这一段配置标签,添加`URIEncoding="utf-8"`,设置默认编码为`UTF-8`  

```xml
<Connector port="8080" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" URIEncoding="utf-8"/>
```
