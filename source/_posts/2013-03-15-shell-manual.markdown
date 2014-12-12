---
layout: post
title: "Shell_manual"
date: 2013-03-15 12:34
comments: true
categories: shell
---
###一些强大的命令
* `!$`

```
!$是一个特殊的环境变量，它代表了上一个命令的最后一个字符串。如：你可能会这样：
$mkdir mydir
$mv mydir yourdir
$cd yourdir
可以改成：
$mkdir mydir
$mv !$ yourdir
$cd !$
```
* `sudo !!`

```
以root的身份执行上一条命令 。
场景举例：比如Ubuntu里用apt-get安装软件包的时候是需要root身份的，我们经常会忘记在apt-get前加sudo。每次不得不加上sudo再重新键入这行命令，这时可以很方便的用sudo !!完事。
（陈皓注：在shell下，有时候你会输入很长的命令，你可以使用!xxx来重复最近的一次命令，比如，你以前输入过，vi /where/the/file/is, 下次你可以使用 !vi 重得上次最近一次的vi命令。）
```

* `cd –`

```
回到上一次的目录 。
场景举例：当前目录为/home/a，用cd ../b切换到/home/b。这时可以通过反复执行cd –命令在/home/a和/home/b之间来回方便的切换。
```

* `‘ALT+.’ or ‘<ESC> .’`

```
热建alt+. 或 esc+. 可以把上次命令行的参数给重复出来。
```

* `^old^new`

```
替换前一条命令里的部分字符串。
场景：echo "wanderful"，其实是想输出echo "wonderful"。只需要^a^o就行了，对很长的命令的错误拼写有很大的帮助。（陈皓注：也可以使用 !!:gs/old/new）
```
* `du -s * | sort -n | tail`

```
列出当前目录里最大的10个文件。
```
* `:w !sudo tee %`

```
在vi中保存一个只有root可以写的文件
```
* `> file.txt`

```
创建一个空文件，比touch短。
```

* 在命令行前加空格，该命令不会进入history里。

* `echo “ls -l” | at midnight`

```
在某个时间运行某个命令。
```
* `ps aux | sort -nk +4 | tail`

```
列出头十个最耗内存的进程
```

* `man ascii`

```
显示ascii码表。
场景：忘记ascii码表的时候还需要google么?尤其在天朝网络如此“顺畅”的情况下，就更麻烦在GWF多应用一次规则了，直接用本地的man ascii吧。
```

* `ssh user@server bash < /path/to/local/script.sh`

```
在远程机器上运行一段脚本。这条命令最大的好处就是不用把脚本拷到远程机器上。
```

* `python -m SimpleHTTPServer`

```
一句话实现一个HTTP服务，把当前目录设为HTTP服务目录，可以通过http://localhost:8000访问 这也许是这个星球上最简单的HTTP服务器的实现了。
```