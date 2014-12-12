---
layout: post
title: "MAC下Android的Eclipse开发环境的搭建"
date: 2013-01-08 23:52
comments: true
categories: android
---
####一．Eclipse的下载

   到网站：[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)，由于我们是用Java开发的所以步骤如下：

1.  找到“Eclipse IDE for java Developers”此处右上角会根据你当前使用的系统自动选择，Mac下就会自动选择位“Mac OS X（Cocoa）”

2.  然后点击右边的“Mac OS X 64bit”（这里我的Pro是i5处理器可以用64位的），根据你的机器也可以选择“Mac OS X 32bit”进行下载。

 

####二．安装ADT

   ***ADT***是Android应用程序的开发环境

1.  点击菜单中的Help ——> Install New Software⋯ ;

2.  在弹出的对话框中有个“Work with”，在右边的输入栏中输入：`https://dl-ssl.google.com/android/eclipse/` 然后下面就会pending出来一个“Developer Tools”，勾选上，然后一路的Next下去就可以安装完成。(如果想开发NDK，顺便选上NDK plugins)

 

####三．设定ADT

   在菜单栏Refactor中如果能看到Android的标签表示ADT安装成功。

1. 下载Android SDK、NDK（通过HomeBrew安装）

2. 安装Android SDK，然后在菜单栏Eclipse —> Preferences（偏好设置）,会弹出一个Preferences对话框，选Android，然后在SDK Loaction中填入刚下载的SDK的路径或者点击右边的Browser选择。

3. 生成模拟器，菜单栏Window —> Android SDK and AVD Manger 会弹出对话框，然后在对话框中选择new开始按自己的需求新建模拟器，至此就大功告成了！


>本该淡淡然~~~