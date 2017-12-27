---
layout:     post
title:      cloudflare的免费https服务,给你的网站加一个S
subtitle:   blog_add-https
date:       2017-12-26
author:     Fe
header-img: img/post-bg-miku1.jpg
catalog: true
tags:
    - Blog
    - Https
---
>关于http和https的区别,可以看我的另一篇文章[HTTP和HTTPS的区别](/2017/12/27/difference-between-http-and-https/)
>参考:[百度](https://baidu.com),[阳光早已褪色](http://blog.csdn.net/u011244202/article/details/57106544),[molunerfinn](https://molunerfinn.com/hexo-travisci-https/)

## 前言  

由于购买了域名, `.github.io` 的证书不能用在我的 [fedemo.top](https://fedemo.top)上面了.

所有我动起了https改造的念头.

刚好,由于域名实名认证这边.百度云没有通知我就直接劫持了我的DNS,虽然认证完很快就解封了,不过还是给我留下了坏印象.  

在寻找其他DNS服务商的时候我发现了[cloudflare](https://www.cloudflare.com/)  

一个提供DNS,并且提供免费HTTPS服务的CDN提供商.  

这里,记录下我如何使用 **cloudflare** 给我的网站加一个S

## 注册  








<br>
