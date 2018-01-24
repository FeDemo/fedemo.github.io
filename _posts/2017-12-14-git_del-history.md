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
:: Checkout 新建一个分支
git checkout --orphan latest_branch

:: Add all the files
git add -A

::Commit the changes 提交,commit message为提交备注,可替换
git commit -am "commit message"

::Delete the branch 删除久的主分支
git branch -D master

::Rename the current branch to master 将新提交的分支更改为主分支
git branch -m master

::Finally, force update your repository 提交到主分支
git push -f origin master

::这是注释.可以直接全部复制到cmd中执行
```

>在cmd中执行上面的脚本
