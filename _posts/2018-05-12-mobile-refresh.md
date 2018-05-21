---
layout:     post
title:      移动端点击返回键，页面不刷新解决方案 (转)
subtitle:   mobile refresh
date:       2018-05-12
author:     老夫风清扬
header-img: img/post-bg-android.jpg
keywords_post:  "移动端点击返回键，页面不刷新解决方案,前端,移动端"
catalog: true
tags:
    - JS
    - 移动端
    - 前端
---
>转自[老夫风清扬](https://blog.csdn.net/weixin_41134409/article/details/79074734)  

今天分享下，在浏览器中点击返回或者前进按钮时，页面不刷新的问题。这个问题存在于移动端居多，尤其是苹果手机。我们一起看看这到底是怎么一回事！   

如果是移动端下，可能有两种情况：   

- 第一种是在自己的app下点击返回的时候页面不刷新，这有可能是你们原生开发人员，只是关闭了当前的一个窗口，也就是说那个窗口是新开的。这种解决方案，老夫只能说找你们的原生开发吧。

- 第二种则是在微信、uc这类的浏览器出现，这是因为浏览器保存了DOM和js的状态，相当于保存了整个页面，这种特性称作 “往返缓存”（back-forward cache，或bfcache）。   

对于这种情况可以用“pageshow”事件来解决，“pageshow”事件表示浏览器展示文档的时候触发，并且是在“onload”事件之后触发。如果浏览器是存在往返缓存机制的话，那么onload事件就只会触发一次，而“pageshow”事件则每次都会触发。这里需要注意“pageshow”事件必须绑定在window这个对象中，如下代码：
```javascript
window.addEventListener('pageshow', function(event) {
    //event.persisted属性为true时，表示当前文档是从往返缓存中获取
    if(event.persisted) location.reload();  
});
```

所以可根据以上方法来让浏览器刷新。
