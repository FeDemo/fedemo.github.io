---
layout:     post
title:      spring笔记--spring3.X与jdk1.8不兼容
subtitle:   hello spring4
date:       2018-03-23
author:     Fe
header-img: img/post-bg-desk.jpg
keywords_post:  "spring4,spring3.X与jdk1.8不兼容,spring,Context initialization failed,java.lang.IllegalArgumentException"
catalog: true
tags:
    - spring
    - Java
---
>参考:[https://www.infoq.com/articles/spring-4-java-8](https://www.infoq.com/articles/spring-4-java-8)

## 前言

在尝试java8的过程中,发现项目在运行的时候回报一个之前没见过一个的错误

 `Context initialization failed`   

在查资料的过程中,发现了是`spring`版本的问题.     

我的项目是使用`spring3.2.0.M2`版本的jar包,而`spring3.x`是不支持`java8`的

## 部分错误信息

2018-03-22 23:38:35,706 ERROR [org.springframework.web.context.ContextLoader] - Context initialization failed  
org.springframework.beans.factory.parsing.BeanDefinitionParsingException: Configuration problem: Failed to import bean definitions from URL location [classpath:conf/spring-mybatis.xml]   
Offending resource: class path resource [conf/applicationContext.xml]; nested exception is    
org.springframework.beans.factory.BeanDefinitionStoreException: Failed to read candidate component class: file     
[D:\IDEA\demo\out\artifacts\demo_Web_exploded\WEB-INF\classes\com\javasm\action\UserInfoAction.class]; nested exception is java.lang.IllegalArgumentException


## 解决方法

spring3.X与jdk1.8不兼容,那么解决的方法就很明显了

1. 升级spring为spring4
2. 将jdk1.8更换为jdk1.7

这里,我的解决方法是将spring升级为spring4,只需要粗暴的将jar包更换就好了

spring jar包下载地址:   

 [https://repo.spring.io/webapp/#/artifacts/browse/tree/General/libs-release-local/org/springframework/spring/4.1.0.RELEASE](https://repo.spring.io/webapp/#/artifacts/browse/tree/General/libs-release-local/org/springframework/spring/4.1.0.RELEASE)
