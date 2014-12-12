---
layout: post
title: "iPhone 系统常用目录路径位置"
date: 2012-08-16 21:09
comments: true
categories: ios
---

1. 【/Applications】 
常用软件的安装目录 
2. 【/private /var/ mobile/Media /iphone video Recorder】 
录像文件存放目录 
3. 【/private /var/ mobile/Media /DCIM】 
相机拍摄的照片文件存放目录 
4. 【/private/var/ mobile /Media/iTunes_Control/Music】 
iTunes上传的多媒体文件（例如MP3、MP4等）存放目录，文件没有被修改，但是文件名字被修改了，直接下载到电脑即可读取。 
5. 【/private /var/root/Media/EBooks】 
电子书存放目录 
6. 【/Library/Ringtones】 
系统自带的来电铃声存放目录（用iTunes将文件转换为ACC文件，把后缀名改成.m4r,用iPhone_PC_Suite传到/Library/Ringtones即可） 
7. 【/private/var/ mobile /Library/AddressBook】 
系统电话本的存放目录。 
8. 【/private /var/ mobile/Media /iphone Recorder】 
录音文件存放目录 
9. 【/Applications/Preferences.app/zh_CN.lproj】 
软件Preferences.app的中文汉化文件存放目录 
10. 【/Library/Wallpaper】 
系统墙纸的存放目录 
11. 【/System/Library/Audio/UISounds】 
系统声音文件的存放目录 
12. 【/private/var/root/Media/PXL】 
ibrickr上传安装程序建立的一个数据库，估计和windows的uninstall记录差不多。 
13. 【/bin】 
和linux系统差不多，是系统执行指令的存放目录。 
14. 【/private/var/ mobile /Library/SMS】 
系统短信的存放目录 
15. 【/private/var/run】 
系统进程运行的临时目录？（查看这里可以看到系统启动的所有进程） 
16. 【/private/var/logs/CrashReporter】 
系统错误记录报告 
17. 【/System/Library/Fonts/Cache】锁屏时钟字体体 ，记得备份原始的字体，然后将 "LockClock.ttf" 复制进去，然后重启或者respring iphone 

---
分割线（补充说明）

---

1. /private/var/mobile 　新刷完的机器，要在这个文件夹下建一个Documents的目录。 
2. /private/var/mobile/Applications 　通过AppStore和iTunes安装的程序都在里面。 
3. /private/var/stash 　这个文件夹下的Applications目录里面是所有通过Cydia和app安装的程序，Ringtones目录里是所有的手机铃音，自制铃音直接拷在里面即可，Themes目录里是所有Winterboard主题，可以手工修改。 
4. /var/mobile/Media/ROMs/GBA 　gpsPhone模拟器存放rom的目录。 
5. /var/mobile/Media/textReader 　textReader看书软件读取的电子书的存放路径。 
6. /System/Library/Fonts/Cache（系统字体目录，要替换的字体放在该目录下，权限644不变） 
7. /private/var/mobile/Media/Maps（离线地图目录，把地图文件夹放到该目录下，文件夹赋予777权限） 
8. /private/var/mobile/Library/Downloads （ipa文件存放目录，用Installous安装） 
9. /private/var/mobile/Library/Keyboard （系统拼音字库文件位置） 
10. /var/stash/Themes.XXXXXX （winterboard主题文件存放路径） 
11. /private/var/mobile/Media/DCIM/999APPLE （系统自带截屏文件存放路径）

---

来给个备份时候常用的路径（摘抄通杀版~）

* /private/var/mobile/Library/AddressBook → 联系人
* /private/var/mobile/Library/CallHistory → 通话记录
* /private/var/mobile/Library/SMS → 短信
* /private/var/mobile/Library/Notes → 备忘录
* /private/var/mobile/Library/Safari → Safari 浏览器保存的书签等 
* /private/var/mobile/Library/Mail → 电子邮件
* /private/var/mobile/Library/MCallShow →信安易来电秀注册文件
* /private/var/mobile/Media/DCIM →照片里面的胶卷
* /private/var/mobile/Media/Photos →照片里面的图片
* /private/var/mobile/Media/Videos →Cycorder摄像机软件拍摄文件保存路径（可以用WINSCP把MP4文件传到这里用它来看哟^_^）
* /private/var/mobile/Library/Preferences com.apple.mobilephone.speeddial.plist →个人收藏（快速拨号）
* /private/var/mobile/Media/Recordings →语音备忘录

> 本该淡淡然~~~