---
layout:     post
title:      阿里巴巴矢量图标库使用笔记
subtitle:   hello iconfont
date:       2018-02-28
author:     Fe
header-img: img/post-bg-desk.jpg
keywords_post:  "图标库,阿里巴巴矢量图标库,阿里妈妈矢量图标,iconfont,Glyphicons"
catalog: true
tags:
    - 前端
---
>免费的图标超市    
>可以拖进购物车的矢量图标    
>阿里妈妈矢量图标平台iconfont+    


## 前言

之前,我的博客是使用Glyphicons提供的图标库.   

通过Bootstrap,可以使用250多个来自 Glyphicon Halflings 的字体图标。Glyphicons Halflings 一般是收费的，但是他们的作者允许 Bootstrap 免费使用。在此,表示感谢    

但是,虽然BootstrapCDN提供免费的CDN加速,允许我们远程载入Glyphicons.可是由于图标库太过庞大,有时会造成过长的载入时间.   

同时里面的图标很多都用不上,在这一过程中,我发现了一款可以自由定制的图标库----iconfont    

她提供了我们像逛淘宝般的图标超市的体验(毕竟是阿里妈妈,一家的)
![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-02-28-hello-iconfont/1.png)

## iconfont+

首先,先上网址----[www.iconfont.cn](http://www.iconfont.cn/)     

iconfont,是由阿里巴巴体验团队打造的，一款设计和前端开发的便捷工具.拥有着很强大且图标内容很丰富的矢量图标库,同时提供自定义图标,图标上传已经下载功能.目前有着70多万个图标  

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-02-28-hello-iconfont/2.png)

## 自定义图标库

>图标超市

登录阿里巴巴矢量图标库（可以使用github账号登录），找到需要的图标，把想要的图标加进购物车

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-02-28-hello-iconfont/3.png)

我们可以下载素材,将购物车的图标下载到本地使用,也可添加到项目方便管理和下次使用

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-02-28-hello-iconfont/1.png)

## iconfont文档

下载下来的项目有着详细的demo和说明文档:    

#### font-class引用    

font-class是unicode使用方式的一种变种，主要是解决unicode书写不直观，语意不明确的问题。   

与unicode使用方式相比，具有如下特点：   

- 兼容性良好，支持ie8+，及所有现代浏览器。
- 相比于unicode语意明确，书写更直观。可以很容易分辨这个icon是什么。
- 因为使用class来定义图标，所以当要替换图标时，只需要修改class里面的unicode引用。
- 不过因为本质上还是使用的字体，所以多色图标还是不支持的。

使用步骤如下：   

>第一步：引入项目下面生成的fontclass代码：

```html
<link rel="stylesheet" type="text/css" href="./iconfont.css">
```

>第二步：挑选相应图标并获取类名，应用于页面：  

```html
<i class="iconfont icon-xxx"></i>
```

"iconfont"是你项目下的font-family。可以通过编辑项目查看，默认是"iconfont"。

## 使用效果  

```html
<i class="icon iconfont icon-rss"></i>
<i class="icon iconfont icon-facebook3"></i>
<i class="icon iconfont icon-tuitetwitter43"></i>
<i class="icon iconfont icon-GitHub"></i>
```
<i class="icon iconfont icon-rss icon-2x"></i>
<i class="icon iconfont icon-facebook3 icon-2x"></i>
<i class="icon iconfont icon-tuitetwitter43 icon-2x"></i>
<i class="icon iconfont icon-GitHub icon-2x"></i>













<br>
