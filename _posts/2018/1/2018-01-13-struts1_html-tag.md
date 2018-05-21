---
layout:     post
title:      struts1的html标签笔记
subtitle:   Struts1_html tags
date:       2018-01-13
author:     Fe
header-img: img/post-bg-p64476688.jpg
keywords_post:  "struts1,html:标签"
catalog: true
tags:
    - Struts1
    - Javaee
    - Java
---
>整理的一些struts1常用的表单标签     
>会不定时更新

## 前言  

最近接触了一个比较老的项目,是用struts1的  

里面的表单用`<html:/>`标签的用的比较多,所以在这里做个归纳总结

## html:form

>JSP  

```html
<html:form action="demoAction.do?method=save" method="post"
    target="actionFrame" styleId="dataForm">
</html:form>
```

>html

```html
<form name="demoActionForm" id="dataForm" method="post"
    action="/demo/demoAction.do?method=save" target="actionFrame">
</form>
```

>说明   

构建一个form表单

***

## html:hidden
>JSP

```html
<html:hidden property="username"/>
```

>html

```html
<input type="hidden" name="username" value="">
```

>说明   

声明一个隐藏的hidden字段,一般用于存储id

***

## html:text
>JSP

```html
<html:text property="username" style="demoStyle"></html:text>
```
>html

```html
<input type="text" name="username" value="" style="demoStyle">
```
账号:<input type="text" name="username" value="" style="demoStyle">

>说明   

一个文本输入框

***

## html:password
>JSP   

```html
<html:password property="password" style="demoStyle"></html:password>
```
>html   

```html
<input type="password" name="password" value="" style="demoStyle">
```

密码: <input type="password" name="password" value="" style="demoStyle">

>说明  

一个密码输入框

***

## html:textarea
>JSP

```html
<html:textarea property="about" cols="93" rows="2" style="demoStyle"></html:textarea>
```
>html   

```html
<textarea name="about" cols="93" rows="2" style="demoStyle"></textarea>
```
详细信息: <textarea name="about" cols="93" rows="2" style="demoStyle"></textarea>

>说明   

一个比较大的文本输入框

***

## html:submit

>JSP

```html
<html:submit property="submit" value="提交"/>
```

>html   

```html
<input type="submit" name="submit" value="提交">
```
<input type="submit" name="submit" value="提交">

>说明   

用于提交表单的按钮

***

## html:reset

>JSP

```html
<html:reset property="reset" value="复位"/>
```

>html

```html
<input type="reset" name="reset" value="复位">
```

<input type="reset" name="reset" value="复位">

>说明   

用于复位的按钮

***

## html:checkbox

>JSP  

```html
<html:checkbox property="checkbox1"/>语文
<html:checkbox property="checkbox2"/>数学
<html:checkbox property="checkbox3"/>英语
```

>html

```html
<input type="checkbox" name="checkbox1" value="on">语文
<input type="checkbox" name="checkbox2" value="on">数学
<input type="checkbox" name="checkbox3" value="on">英语
```

<input type="checkbox" name="checkbox1" value="on">语文
<input type="checkbox" name="checkbox2" value="on">数学
<input type="checkbox" name="checkbox3" value="on">英语

>说明   

多选框checkbox

***

## html:multibox

>JSP

```html
<html:multibox property="multiboxs" value="1"/>语文
<html:multibox property="multiboxs" value="2"/>数学
<html:multibox property="multiboxs" value="3"/>英语
```

>html

```html
<input type="checkbox" name="multiboxs" value="1">语文
<input type="checkbox" name="multiboxs" value="2">数学
<input type="checkbox" name="multiboxs" value="3">英语
```

<input type="checkbox" name="multiboxs" value="1">语文
<input type="checkbox" name="multiboxs" value="2">数学
<input type="checkbox" name="multiboxs" value="3">英语

>说明   

`html:multibox`标签和`html:checkbox`标签类似,解析成html代码都是`checkbox`

但是multibox中的每个checkbox的name都相同,而`html:checkbox`中的每个checkbox的name都不同

意味着`multibox`在`ActionForm`中是以数组的形式存在,而`checkbox`则是以单个的值存在

***

## html:radio

>JSP

```html
<html:radio property="radios" value="1"/>语文
<html:radio property="radios" value="2"/>数学
<html:radio property="radios" value="3"/>英语
```

>html

```html
<input type="radio" name="radios" value="1">语文
<input type="radio" name="radios" value="2">数学
<input type="radio" name="radios" value="3">英语
```

<input type="radio" name="radios" value="1">语文
<input type="radio" name="radios" value="2">数学
<input type="radio" name="radios" value="3">英语

>说明

***

单选款radio

## html:select

>JSP  

```html
<html:select property="selectDemo" size="1">
    <html:option value="value1">语文</html:option>
    <html:option value="value2">数学</html:option>
    <html:option value="value3">英语</html:option>
</html:select>
```

>htmp

```html
<select name="selectDemo" size="1">
    <option value="value1">语文</option>
    <option value="value2">数学</option>
    <option value="value3">英语</option>
</select>
```
科目:
<select name="selectDemo" size="1">
    <option value="value1">语文</option>
		<option value="value2">数学</option>
	  <option value="value3">英语</option>
</select>

>说明

下拉选择表单控件

***

## html:file

>JSP

```html
<html:file property="filedemo" />
```

>html

```html
<input type="file" name="filedemo" value="">
```
<input type="file" name="filedemo" value="">

>说明

表单文件上传控件

***
