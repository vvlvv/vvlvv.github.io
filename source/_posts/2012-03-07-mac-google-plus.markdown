---
layout: post
title: "mac 不翻墙访问 google+"
date: 2012-03-07 14:04
comments: true
categories: mac
---
1. 打开应用程序
2. 打开terminal
3. 输入sudo nano /etc/hosts
4. 输入你的用户密码（此时输入密码屏幕不会显示），回车即可修改
5. 修改完后ctrl+x保存 退出

在hosts文件末添加：

{% codeblock lang:sh %}
#google plus
74.125.230.107 plus.google.com
209.85.175.132 images1-focus-opensocial.googleusercontent.com
209.85.175.132 images2-focus-opensocia2.googleusercontent.com
209.85.175.132 s2.googleusercontent.com
209.85.143.132 lh1.googleusercontent.com
209.85.175.132 lh1.googleusercontent.com
209.85.143.132 lh2.googleusercontent.com
209.85.175.132 lh2.googleusercontent.com
209.85.143.132 lh3.googleusercontent.com
209.85.175.132 lh3.googleusercontent.com
209.85.175.132 lh4.googleusercontent.com
209.85.143.132 lh4.googleusercontent.com
209.85.143.132 lh5.googleusercontent.com
209.85.175.132 lh5.googleusercontent.com
209.85.143.132 lh6.googleusercontent.com
209.85.175.132 lh6.googleusercontent.com
{% endcodeblock %}

保存后即可正常访问Google+.

> 本该淡淡然~~~