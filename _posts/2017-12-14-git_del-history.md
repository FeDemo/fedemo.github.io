---
layout:     post
title:      git仓库删除所有提交历史记录，还你一个干净的git仓库
subtitle:   git_del history
date:       2017-12-14
author:     Fe
header-img: img/post-bg-ios9-web.jpg
keywords_post:  "git,历史,history"
catalog: true
tags:
    - Git
---
> 参考:[yanchengyc](http://blog.csdn.net/yc1022/article/details/56487680)   
>一个干净的git仓库


一个项目从创建到框架搭建完成,在这过程中会产生很多不必要的   

同时,还会有很多包括密码在内的不想让别人看到的敏感信息

那么,如何删除这些历史记录，形成一个干净的git仓库，并且保持代码不变呢？

***

```

git checkout --orphan latest_branch

git add -A

git commit -am "commit message"

git branch -D master

git branch -m master

git push -f origin master

```

>在项目的目录运行上面的命令,命令结束后按下回车
