---
layout: post
title: "info.plist常用key介绍"
date: 2012-08-24 16:41
comments: true
categories: ios
---

* UIRequiresPersistentWiFi 在程序中弹出wifi选择的key（系统设置中需要将wifi提示打开）
* UIAppFonts 内嵌字体[详细介绍](http://www.minroad.com/?p=412)
* UIApplicationExitsOnSuspend 程序是否在后台运行，自己在进入后台的时候exit(0)是很傻的办法
* UIBackgroundModes 后台运行时的服务，具体看iOS4的后台介绍
* UIDeviceFamily array类型（1为iPhone和iPod touch设备，2为iPad)
* UIFileSharingEnabled 开启itunes共享document文件夹
* UILaunchImageFile 相当于Default.png（更名而已）
* UIPrerenderedIcon icon上是否有高光
* UIRequiredDeviceCapabilities 设备需要的功能[具体点击这里查看](http://developer.apple.com/library/mac/#documentation/General/Reference/InfoPlistKeyReference/Articles/iPhoneOSKeys.html%23//apple_ref/doc/uid/TP40009252-SW3)
* UIStatusBarHidden 状态栏隐藏（和程序内的区别是在于显示Default.png已经生效）
* UIStatusBarStyle 状态栏类型
* UIViewEdgeAntialiasing 是否开启抗锯齿
* CFBundleDisplayName app显示名
* CFBundleIconFile、CFBundleIconFiles 图标
* CFBundleName 与CFBundleDisplayName的区别在于这个是短名，16字符之内
* CFBundleVersion 版本
* CFBundleURLTypes 自定义url，用于利用url弹回程序
* CFBundleLocalizations 本地资源的本地化语言，用于itunes页面左下角显示本地话语种
* CFBundleDevelopmentRegion 也是本地化相关，如果用户所在地没有相应的语言资源，则用这个key的value来作为默认

> 本该淡淡然~~~