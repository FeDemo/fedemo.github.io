---
layout:     post
title:      jQuery笔记--选择器
subtitle:   jQuery selectors
date:       2018-03-31
author:     Fe
header-img: img/post-bg-2015.jpg
keywords_post:  "jquery,jquery选择器,jquery对象和dom对象,jquery对象,dom对象,前端,$,标签,元素"
catalog: true
tags:
    - jquery
    - 前端
    - JS
---
>参考:  [w3c](http://www.w3school.com.cn)  , **jquery.api.3.2.1**

## jQuery 选择器  

| 选择器 | 实例 | 选取 |
| #id | `$("#myDiv")` | id="myDiv" 的元素 |
| _element_ | `$("div")` | 所有 <div> 元素 |
| .class | `$(".myClass")` | 所有 class="myClass" 的元素 |
| * | `$("*")` | 所有元素 |
| selector1,selector2,selectorN  | `$("div,span,p.myClass")`  | 所有匹配这三个条件的元素  |
|  this | `$(this)`  | 当前的html元素  |
|   |   |   |
| [attribute]  | `$("div[id]")`  | 所有含有 id 属性的 div 元素  |
|  [attribute=value] | `$("input[name='newsletter']")`  |  所有 name 属性是 newsletter 的 input 元素 |
|  [attribute!=value] | `$("input[name!='newsletter']")`  |  所有 name 属性不是 newsletter 的 input 元素 |
|  [attribute^=value] | `$("input[name^='news']")`  | 所有 name 以 'news' 开始的 input 元素  |
|  [attribute$=value] |  `$("input[name$='letter']")` | 所有 name 以 'letter' 结尾的 input 元素  |
| [attribute*=value]  | `$("input[name*='man']")`  | 所有 name 包含 'man' 的 input 元素  |
| [selector1][selector2][selectorN]  | `$("input[id][name$='man']")`  | 所有含有 id 属性，并且它的 name 属性是以 man 结尾的元素  |
|   |   |   |
| ancestor descendant  | `$("form input")`  | form表单下的所有input元素  |
| parent > child | `$("form > input")`  | 表单中所有的子级input元素  |
| prev + next  | `$("label + input")`  | 所有跟在 label 后面的 input 元素  |
| prev ~ siblings  | `$("form ~ input")`  | 所有与表单同辈的 input 元素  |
|   |   |   |
| :first | `$("p:first")` | 第一个 <p> 元素 |
| :last | `$("p:last")` | 最后一个 <p> 元素 |
| :even | `$("tr:even")` | 所有偶数 <tr> 元素 |
| :odd | `$("tr:odd")` | 所有奇数 <tr> 元素 |
|   |   |   |
| :eq(_index_) | `$("ul li:eq(3)")` | 列表中的第四个元素（index 从 0 开始） |
| :gt(_no_) | `$("ul li:gt(3)")` | 列出 index 大于 3 的元素 |
| :lt(_no_) | `$("ul li:lt(3)")` | 列出 index 小于 3 的元素 |
| :not(_selector_) | `$("input:not(:empty)")` | 所有不为空的 input 元素 |
|   |   |   |
| :header | `$(":header")` | 所有标题元素 <h1> - <h6> |
| :animated |   | 所有动画元素 |
|   |   |   |
| :contains(_text_) | `$(":contains('W3School')")` | 包含指定字符串的所有元素 |
| :empty | `$(":empty")` | 无子（元素）节点的所有元素 |
| :hidden | `$("p:hidden")` | 所有隐藏的 <p> 元素 |
| :visible | `$("table:visible")` | 所有可见的表格 |
|   |   |   |
| _attribute_ | `$("href]")` | 所有带有 href 属性的元素 |
| _attribute_=_value_ | `$("href='#']")` | 所有 href 属性的值等于 "#" 的元素 |
| _attribute_!=_value_ | `$("href!='#']")` | 所有 href 属性的值不等于 "#" 的元素 |
| _attribute_$=_value_ | `$("href$='.jpg']")` | 所有 href 属性的值包含以 ".jpg" 结尾的元素 |
|   |   |   |
| :input | `$(":input")` | 所有 `<input>` 元素 |
| :text | `$(":text")` | 所有 type="text" 的 `<input>` 元素 |
| :password | `$(":password")` | 所有 type="password" 的 `<input>` 元素 |
| :radio | `$(":radio")` | 所有 type="radio" 的 `<input>` 元素 |
| :checkbox | `$(":checkbox")` | 所有 type="checkbox" 的 `<input>` 元素 |
| :submit | `$(":submit")` | 所有 type="submit" 的 `<input>` 元素 |
| :reset | `$(":reset")` | 所有 type="reset" 的 `<input>` 元素 |
| :button | `$(":button")` | 所有 type="button" 的 `<input>` 元素 |
| :image | `$(":image")` | 所有 type="image" 的 `<input>` 元素 |
| :file | `$(":file")` | 所有 type="file" 的 `<input>` 元素 |
|   |   |   |
| :enabled | `$(":enabled")` | 所有激活的 `<input>` 元素 |
| :disabled | `$(":disabled")` | 所有禁用的 `<input>` 元素 |
| :selected | `$(":selected")` | 所有被选取的 `<input>` 元素 |
| :checked | `$(":checked")` | 所有被选中的 `<input>` 元素 |

## jquery对象和dom对象

>jquery对象的实质   

jquery对象其实是一个javascript的数组，这个数组对象包含125个方法和4个属性   

4个属性分别是   

- `jquery`     当前的jquery框架版本号

- `length`     指示该数组对象的元素个数

- `context`    一般情况下都是指向HtmlDocument对象   

- `selector`   传递进来的选择器内容  如：#yourId或.yourClass等  

>jquery对象和dom对象的转换  

```javascript
var jq=$("#yourId");//jquery对象
var dom=document.getElementById("yourId");//dom对象
```
`jq[0]`就是`HtmlElement`元素,和`dom`是等价的,也就是
```javascript
var jq=$("#yourId");//jquery对象
var dom=jq[0];//dom对象
```
同时
```javascript
var dom=document.getElementById("yourId");//dom对象
var jq=$(dom);//jquery对象
```
将dom对象包一层`$()`后,就成了`jquery`对象  
