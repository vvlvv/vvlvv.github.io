---
layout: post
title: "QQ weibo error clientip:127.0.0.1"
date: 2012-03-09 13:21
comments: true
categories: ios
---
在开发网站成为开发者后 创建应用程序，得到饿了appkey和appsecret，放至程序中，转发得到如下错误信息，
{% codeblock lang:objc %}
{
    data = "<null>";
    errcode = 1;
    msg = "error clientip:127.0.0.1";
    ret = 1;
}
{% endcodeblock %}

腾讯针对这个错误给出的解释是“调用接口时所填写的clientip错误，必须为用户侧真实ip，不能为内网ip、以127及255开头的ip ”， 将clientip指定为用户此时的ip就对了，成功发送.

IOS 获取外网真实IP方法如下：
{% codeblock lang:objc %}
NSError *error;
NSURL * ipURL = [NSURL URLWithString:@"http://automation.whatismyip.com/n09230945.asp"];
NSString * ip_ = [NSString stringWithContentsOfURL:ipURL encoding:NSUTF8StringEncoding error:&error];
{% endcodeblock %}

> 本该淡淡然~~~