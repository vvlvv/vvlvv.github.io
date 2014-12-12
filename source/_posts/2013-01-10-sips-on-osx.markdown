---
layout: post
title: "在 OS X 系统中使用 sips 命令批量处理图片"
date: 2013-01-10 12:54
comments: true
categories: mac
---
苹果系统自带的图片处理命令***sips***。

比如，你想要将某文件夹的 n 张大尺寸JPG图片都缩小成宽度为600px的图片，高度自动按比例缩放。那么命令则为(假设文件夹的路径为 ~/Desktop/Test)：

    sips -Z 600 ~/Desktop/Test/*.JPG

执行完成之后，你桌面上Test文件夹中的所有JPG图片都缩小城宽度为600px的小尺寸版本了。另外，sips 还有很多功能有待你挖掘，比如你还可以指定高度和宽度(注意z需要小写)：

    sips -z 300 600 ~/Desktop/Test/*.JPG

你还可以用 sips 命令批量旋转图片，默认旋转方式为顺时针，下面是将图片顺时针旋转90度的方法：

    sips -r 90 ~/Desktop/Test/*.JPG

其实，你甚至可以以不规则的角度旋转，比如旋转120度，大家自己试试是什么效果吧。

还可以用来翻转图片，不管是水平翻转还是垂直翻转都可以。水平翻转命令为：

    sips -f horizontal ~/Desktop/Test/*.JPG

垂直翻转命令为：

    sips -f vertical ~/Desktop/Test/*.JPG

> 本该淡淡然~~~