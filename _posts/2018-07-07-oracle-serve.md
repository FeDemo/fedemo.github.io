---
layout:     post
title:      oracle服务笔记
subtitle:   oracle serve
date:       2018-7-07
author:     Fe
header-img: img/post-bg-rwd.jpg
keywords_post:  "oracle服务笔记,oracle,开启关闭Oracle服务脚本,bat"
catalog: true
tags:
    - oracle
---
>参考[百度文库](https://wenku.baidu.com/view/5e07d4b076a20029bd642ded.html)

## 前言  

## oracle服务

Oracle11g安装后，一般会有下面这七个服务   

其中, `OracleMTSRecoveryService` , `OracleOraDb11g_home1TNSListener` , `OracleServiceORCL是默认启动的` , `OracleJobSchedulerORCL` 是默认自动禁止的,其余的默认为手动操作   

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-07-07-oracle-serve/1.png)

如果只需要使用oracle自带的sqlplus连接数据库的话,那么只需要开启 `OracleServiceORCL` 这个服务就可以了   

当需要使用plsql等第三方工具或本地项目需要连接时则需要开启监听 `OracleOraDb11g_home1TNSListener`
#### 1.OracleDBConsoleorcl

Oracle数据库控制台服务，orcl是Oracle的实例标识，默认的实例为orcl。在运行Enterprise Manager(企业管理器OEM)的时候，需要启动这个服务。(非必须启动)

#### 2.OracleJobSchedulerORCL

Oracle作业调度(定时器)服务，ORCL是Oracle实例标识。(非必须启动)

#### 3.OracleMTSRecoveryService

服务端控制。该服务允许数据库充当一个微软事务服务器MTS、COM/COM+对象和分布式环境下的事务的资源管理器。(非必须启动)

#### 4.OracleOraDb11g_home1ClrAgent

Oracle数据库.NET扩展服务的一部分。 (非必须启动)

#### 5.OracleOraDb11g_home1TNSListener

监听器服务，服务只有在数据库需要远程访问的时候才需要。(非必须启动)

#### 6.OracleServiceORCL

数据库服务(数据库实例)，是Oracle核心服务该服务，是数据库启动的基础， 只有该服务启动，Oracle数据库才能正常启动。(必须启动)

#### 7.OracleVssWriterORCL
>Oracle ORCL VSS Writer Service

能够让存储基础设备(比如磁盘,阵列等)创建高保真的时间点映像,即映射拷贝(shadow copy)。它可以在多卷或者单个卷上创建映射拷贝,同时不会影响到系统的系统能。(非必须启动)

## 开启关闭Oracle服务脚本

由于只是Oracle的服务比较重(卡),我们可以把其的各项服务都设置为手动开启,只在需要测试的时候打开
![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-07-07-oracle-serve/2.png)  

附上批处理代码,复制到文本后把后缀名改成`bat`就可以用了

>oracle_start.bat

```
@echo off  
%1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit  
cd /d "%~dp0"  
net start "OracleOraDb11g_home1TNSListener"
net start "OracleServiceORCL"
```

> oracle_stop.bat  

```
@echo off  
%1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit  
cd /d "%~dp0"  
net stop "OracleServiceORCL"
net stop "OracleOraDb11g_home1TNSListener"
```

其中
```
@echo off  
%1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit  
cd /d "%~dp0"  
```
这段命令是获得管理员权限.win10的系统需要先获得权限才可以对服务进行操作










<br>
