---
layout:     post
title:      struts1和struts2的特点和区别(转)
subtitle:   difference between struts1 and struts2
date:       2018-01-09
author:     Simon丶Ma
header-img: img/post-bg-miku2.jpg
keywords_post:  "struts1,struts2,struts1和struts2的区别"
catalog: true
tags:
    - Struts1
    - Struts2
    - Javaee
---

>转自<a href="http://blog.csdn.net/u011225629/article/details/47856517" target="view_window">Simon丶Ma</a>   

## 一.MVC的特点   

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-01-09-difference-between-struts1-and-struts2/1.png)
- 多个视图可以对应一个模型。按MVC设计模式，一个模型对应多个视图，可以减少代码的复制及代码的维护量，一旦模型发生改变，也易于维护。   

- 模型返回的数据与显示逻辑分离。模型数据可以应用任何的显示技术，例如，使用JSP页面、Velocity模板或者直接产生Excel文档等。   

- 应用被分隔为三层，降低了各层之间的耦合，提供了应用的可扩展性。   

- 控制层的概念也很有效，由于它把不同的模型和不同的视图组合在一起，完成不同的请求。因此，控制层可以说是包含了用户请求权限的概念。   

- MVC更符合软件工程化管理的精神。不同的层各司其职，每一层的组件具有相同的特征，有利于通过工程化和工具化产生管理程序代码。



## 二.Struts1的特点   

Struts 1以ActionServlet作为核心控制器，由ActionServlet负责拦截用户的所有请求。Struts 1框架有3个重要组成部分：**Action** 、**ActionForm** 和 **ActionForward** 对象。    

>ActionForm  

ActionForm必须实现ActionForm的基类,设计上并不是真正的POJO   

>ActionForward   

ActionForward就是一个逻辑视图，通过在配置文件中定义ActionFoward的映射，完成逻辑视图名和实际视图资源之间的映射    

>Action   

Struts 1的Action类与Struts 2的Action类有一定的类似性，都通过调用execute方法来处理用户请求。但最大的区别在于Struts 1 Action的execute方法与Servlet API耦合(ActionServlet继承自HttpServlet)，但Struts 2 Action类的execute方法无需与Servlet API耦合。

#### struts1的缺陷   

1. 只支持JSP作为表现层技术,不能与Velocity,FreeMarker等技术整合
2. 与Servlet API严重耦合,难于测试
一个exute有四个参数ActionMapping、ActionForm、HttpServletRequest和HttpServletResponse,初始化困难.
3. 侵入式设计,严重依赖于Struts1API,如如ActionMapping、ActionForm和ActionForward类.一旦系统需要重构时,这些类完全没有利用价值,导致较低的代码复用.

## 三.Struts2的特点  

struts2核心控制器：FilterDispatcher   

Struts 2用于处理用户请求的Action实例，并不是用户实现的业务控制器，而是Action代理——因为用户实现的业务控制器并没有与Servlet API耦合，显然无法处理用户请求。而Struts 2框架提供了系列拦截器，该系列拦截器负责将HttpServletRequest请求中的请求参数解析出来，传入到Action中，并回调Action 的execute方法来处理用户请求。显然，上面的处理过程是典型的AOP（面向切面编程）处理方式。

#### Struts2 Action有以下特点

- Action类完全是一个POJO，因此具有很好的代码复用性。
- Action类无需与Servlet API耦合，因此进行单元测试非常简单。
- Action类的execute方法仅返回一个字符串作为处理结果，该处理结果可映射到任何的视图，甚至是另一个Action。

#### Struts 2的配置文件有两份  

- 配置Action的struts.xml文件。
- 配置Struts 2全局属性的struts.properties文件。

下面是struts.xml配置文件的示例：





## 四、区别和对比  

#### 1、Servlet依赖性

由于Action在被调用的时候，HttpServletRequest和HttpServletResponse被传递到execute()方法，struts1的Action对Servlet API有依赖  在struts2中，Action就不会对容器有依赖性了，因为struts2的Action是由简单的POJO组成，在struts2中，Servlet上下文以简单的Map的形式使得Action可以得到独立的测试，如果需要，struts2也可以访问原始的请求与响应。

#### 2、 Action类

struts1要求action类 **继承** 一个基类，struts2 Action要求 **继承** 一个基类的同时也允许实现 **接口** 的方式来实现

#### 3、验证

struts1和struts2都支持通过validate方法的手动验证，struts1使用ActionForm中的validate方法，而struts2支持通过Validate方法和Xwork校验框架的手动验证

#### 4、线程

struts1是单例模式的并且必须是线程安全的，因为仅有一个Action的实例来处理所有请求，而struts2为每一个请求产生一个实例

#### 5、易测性

struts1一个主要问题是execute方法暴露了Servlet API，一个叫Struts TestCase的第三方扩展，提供了一个struts1测试用的模拟对象，但是struts2中，Action可以经由创建Action实例，设置属性，和调用方法来得到测试

#### 6、获取输出

struts1使用ActionForm来捕获输入，而所有的ActionForm需要继承一个框架依赖的基类，由于javabean不能当作ActionForm来用，开发人员不得不创建冗繁的类来获取出入，不过struts2用Action属性，这避免了需要创建第二个输入对象

#### 7、表达式语音

struts1与JSTL整合，struts2不仅支持jstl 还支持OGNL

#### 8、将绑定值到视图中

在视图层，struts1使用标准的JSP来绑定对象到页面上下文来访问，然而struts2使用一种叫值栈的技术，这使得标签可以访问值而不需将视图与正在呈递的对象类型连接起来，值栈允许重用一些属性名相同但类型不同的视图类型

#### 9、类型转换

通常struts1的ActionForm属性都是string类型的，struts1使用Commons-Beanutils进行类型转换，这些针对每一个类的类型转换无法为每一个实例配置，然而struts2使用OGNL来进行类型转换，框架包含了针对基础类型，常见对象类型与原始类型的转换器

#### 10、Action执行控制

struts1支持每一个模块的请求处理器的分离，但是同一模块下的所有Action必须共享相同的生命周期，struts2支持通过拦截器栈为每一个Action创建不同的生命周期，自定义栈可以视需要对不同的Action使用
