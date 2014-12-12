---
layout: post
title: "HockeyKit run on OSX"
date: 2013-01-29 16:01
comments: true
categories: mac
---
### 引子

今天工作不是很忙，闲的无聊瞎逛。突然间发现了[TestFight](https://testflightapp.com/)这个东东。很好用，但是弊端也很明显。每次打包ipa有20M+，上传服务器，进行OTA安装又要重新下载，太浪费时间了。不适合公司内部用。这个东东适合一些业余的团队在业余的时间做开发。及时性要求不高。google了之后发现还有个HockeyKit。
### HockeyKit
公司现在用的是HockeyApp，这个项目之前是开源的，后来变收费了。所以我们就一直停留在老的版本，功能很有限。突然发现了新大陆HockeyKit，免费开源。支持android和ios。Nice ^_^  马上搭建起来。现在我的mac上做测试，成功后再搭建到公司服务器上。

1. 项目地址[https://github.com/TheRealKerni/HockeyKit](https://github.com/TheRealKerni/HockeyKit)，克隆到本地，切换到master。目录有server，client，demo。只需要server就可以了。
2. 按照[wiki](https://github.com/TheRealKerni/HockeyKit/wiki/Server)的介绍安装，首先需要一个支持php5的服务器。lion自带了apache，修改httpd.conf，让apache支持php。（lion 需要命令来启动apache `sudo apachectl start`）
   * 确保你的服务器的httpd.conf 中 AllowOverride All ，以支持HockeyKit Server中子目录的配置重载
   * 确保服务的rewirte可用（lion默认开启 LoadModule rewrite_module libexec/apache2/mod_rewrite.so)
3. 其他的按照文档进行就可以了。大功告成， ^_^  最后点击install application，如果出现alertview提示错误，重新回到步骤2检查一下是否设置了AllowOverride All。

> 本该淡淡然