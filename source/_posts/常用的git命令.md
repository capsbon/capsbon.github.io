---
title: 常用的git命令
date: 2018-03-19 22:09:44
tags:
categories: tools
---

设置用户名邮箱

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

提交

```
#将“当前修改”移动到暂存区(stage)
# git add .  将当前所有修改添加到暂存区
$ git add somfile.txt
#将暂存区修改提交
$ git commit -m "Add somfile.txt."
```

状态

```
$ git status
$ git diff
```

远程操作

```
$ git remote add origin git@github.com:michaelliao/learngit.git
# 第一次推送，-u(--set-upstream)指定默认上游
$ git push -u origin master
$ git push origin master
```



拉取远程仓库

```
$ mkdir git_work

$ cd git_work

$ git init

$ git clone http://myrepo.xxx.com/project/.git 

$ cd project

$ git branch -a #列出所有分支名称如下：
           remotes/origin/dev
           remotes/origin/release

$ git checkout -b dev origin/dev  在本地新建并切换分支
```

