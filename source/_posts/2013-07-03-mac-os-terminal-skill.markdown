---
layout: post
title: "mac os terminal skill"
date: 2013-07-03 10:35
comments: true
categories: mac
---

##control+u

如果你在一条终端命令中发现有输入错误的话，那么用 control+u 快捷键可以直接删除这一整条命令，然后你就可以重新输入。

##mkdir

很多人可能会很熟悉在 mkdir 是在「终端」中创建文件夹的工具，比如mkdir ./abc，即可在当前目录创建一个名为 abc 的文件夹。但如果想要建立更多层级的目录呢？就需要用 mkdir -p 命令来解决，比如：

```
mkdir -p ./abc/123/guomii/xxx
```
##!!

有时候，你写了一条长长的命令，按回车之后发现没有执行权限，需要在命令前添加 sudo，这时你可能要崩溃。不过其实可以用 `sudo !!` 这条命令来解决，它执行的效果和 sudo {上一条命令} 是一样的。

另外，! 在「终端」中还有一个妙用——它可以用来执行你最后一次以特定字母开头的命令。比如你在一个「终端」会话中已经执行过ls,mkdir,find,chown 等多条命令。这时你可以用 !l 来执行 ls，用 !f 来执行 find…大家都看懂了吧？(very cool)

##history

用 history 命令可以显示你最近执行过的命令历史记录，你还可以指定显示条数，比如 history 20即可显示最近的20条命令历史记录。此外，你还可以筛选包含特定字符的命令，比如用 `history | grep mk`，就可以只显示历史记录中包含 mk 的命令。

##&&

&& 可以将两条命令合并成一条命令，其实我们在之前的文章中，已经多次应用过这种写法了，大家可以返回去看看。

##reset

reset 的作用很简单——将目前「终端」屏幕上的内容清空，就好像刚刚打开终端一样。（不如新建一个标签，然后关掉之前的，感觉这样更快捷。）

其实输入命令远没有快捷键方便，“control+l” 可以清屏，"command+k"可以全部清除。