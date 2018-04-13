---
layout:     post
title:      解决github屏蔽百度爬虫的问题
subtitle:   hello coding
date:       2018-01-26
author:     Fe
header-img: img/post-bg-coding.png
keywords_post:  "coding,github,coding-page,github-pages,解决github-pages无法被百度抓取的问题"
catalog: true
tags:
    - Blog
---
>coding初体验   
>coding和github的page服务  
>coding和github的区别    
>使用coding的page服务解决github-pages无法被百度抓取的问题    

## 前言  

由于github屏蔽了百度爬虫,导致我们的文章很难被百度所收录   

对此github官方是这样说的 : 由于百度爬虫爬得太猛烈，已经对很多Github用户造成了可用性的问题了，而禁用百度爬虫这一举措可能会一直持续下去。  

那么,我们搭建在gouhub上的文章是不是就再也不能被百度收录然后被搜索出来了呢?   

当然不是!  

那么,我们应该怎么做呢?

## 搭建镜像网站   

关于如何解决github-pages无法被百度抓取的问题  

在我逛CSDN以及知乎时,看到很多大牛他们所提出的解决方案都有一个一致性:  

那就是搭建镜像网站,让来自百度爬虫的ip去爬镜像网站,以达到百度爬虫的正常抓取的目的.画个草图,大概是这样的:  

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-01-26-hellow-coding/1.png)  

画的有点草......将就着看吧  

## coding

最开始我是找了一些传统提供CDN镜像服务的平台,可是我发现都有着诸多限制.在这过程中,我了解到了coding.   

可以简单的认为是一家国内的github,同样提供git仓库和page服务.与github不同的是,coding没有对百度爬虫进行屏蔽.这样意味着我们可以使用coding搭建我们的镜像网站,然后让百度去爬我们搭建在coding上的文章,从而解决我们的问题   

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-01-26-hellow-coding/5.png)

先让我们看看coding和github的区别   

#### coding和github的差别  

首先,关于github和coding的区别可以看下这篇coding官方文章[为什么 Coding 不是中国的 Github ？](https://blog.coding.net/blog/why-coding-does-not-equals-github)   


那么我就在这里总结一下github和coding的区别吧(谨代表个人意见)  

>coding的优点  

- 提供自定义域名的https服务,虽然就算使用github也可以通过cloudflare的https服务加上一个绿色小锁......
- 由于coding是国内服务器,在速度上会快上很多,不论在git的pull和clone上还是page服务上   
- coding的免费用户就用于5个私人仓库,虽然我用不上  

>github的优点

- 在page服务上github要比coding限制少的多.coding必需要在首页加上 Hosted by **Coding Pages** 的文字版或者图片版.不然就会给你的网站插广告,这点比较难受
- 个人主页对比coding会更加直观简洁,各个项目的情况会比coding更清晰,当然这和我还没看习惯coding的原因也有关系
- 逼格要比coding高,github在我看来是一个全球性的程序员社交平台,这一点是coding远远没办法比的
- 稳定性上github更胜一筹,coding虽然快可是有时候会宕机(来自网友评论)

#### 使用coding搭建镜像网站  

了解完coding,就该我们使用coding来搭建我们的镜像网站了.   

先上 [官方教程](https://coding.net/pages/),然后这是githubpage的[搭建教程](https://fedemo.top/2017/12/08/blog_re0/),在这里就不细说了,这里主要说一下如何保持github和coding仓库的同步.

>通过配置config,同步更新多个代码仓库   

在我们的项目文件中找到`.git/config`文件,打开  

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-01-26-hellow-coding/2.png)


```
[remote "origin"]
	url = https://git.coding.net/fedemo/blog.git
	url = https://github.com/FeDemo/fedemo.github.io.git
```
找到我们在github上的url,然后只需要在我们原来的url的地方再加一条url记录就可以达到一次`PUSH`同时同步两个仓库的效果了   

## 配置DNS信息   

现在很多DNS都有智能DNS解析功能,这里我就说下我用的百度云解析,同时推荐DNSPOD

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-01-26-hellow-coding/3.png)

默认的是github的路线,然后来自百度搜索引擎的就走coding的线路,这样就完美的解决github-pages无法被百度抓取的问题了  

## 成果

百度站长工具抓取诊断结果

![](https://raw.githubusercontent.com/FeDemo/img_gitalk/master/2018-01-26-hellow-coding/4.png)


现在,完美只要做好文章的编写,然后时不时的发发外链,就可以静待百度的收录的

END
