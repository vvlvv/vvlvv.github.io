---
layout: post
title: "git log geek"
date: 2013-06-21 14:21
comments: true
categories: git
---

* 打开.gitconfig文件(该文件在用户目录下面)

```
vim .gitconfig
```
* 配置gitconfig

在打开的文件中加入下面的命令：

```
[alias]
       lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```


* 查看配置后的log

```
git lg
```

* 在log中查看哪一行被修发了

```
git lg -p
```