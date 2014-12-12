---
layout: post
title: "wget tutorials"
date: 2013-06-27 15:05
comments: true
categories: tools
---

Wget是一种很好用的因特网下载工具，他具有的很多特性是其他工具所不能比拟的，再者他是一个轻量级可配置的下载工具。

本文结合例子介绍Windows下wget的多种下载方法和用途。

1、用Wget下载单个文件

下载的时候会显示：

　　~文件的大小、连接状态、连接地址以及文件的大小

　　~保存的名称

　　~下载进度条

　　~下载速度、时间，还有多少未下载

例如我下载editplus时输入

D:\Hack stuff\wget>wget http://software-files-a.cnet.com/s/software/12/32/81/47/
epp331.exe?token=1329413178_4553efa847829f3ecef10c1bc256fcc0&lop=link&ptype=3001
&ontid=2352&siteId=4&edId=3&spi=537d5d5485f688682d82c481c4fb15a1&pid=12328147&ps
id=10018241&&fileName=epp331.exe
则下载时会显示以下内容

D:\Hack stuff\wget>wget http://software-files-a.cnet.com/s/software/12/32/81/47/
epp331.exe?token=1329413178_4553efa847829f3ecef10c1bc256fcc0&lop=link&ptype=3001
&ontid=2352&siteId=4&edId=3&spi=537d5d5485f688682d82c481c4fb15a1&pid=12328147&ps
id=10018241&&fileName=epp331.exe
--2012-02-16 15:28:50--  http://software-files-a.cnet.com/s/software/12/32/81/47
/epp331.exe?token=1329413178_4553efa847829f3ecef10c1bc256fcc0
Resolving software-files-a.cnet.com... 204.2.171.33, 204.2.171.35
Connecting to software-files-a.cnet.com|204.2.171.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1766464 (1.7M) [application/octet-stream]
Saving to: `epp331.exe@token=1329413178_4553efa847829f3ecef10c1bc256fcc0'

18% [======>                                ] 335,238     20.5K/s  eta 64s
 

2、用Wget-O下载可以为下载的文件指定另外一个名字

默认情况下wget会用最后的斜线后面的所有字符来命名下载下来的文件，如上例所示保存的文件名为

Saving to: `epp331.exe@token=1329413178_4553efa847829f3ecef10c1bc256fcc0'
这不是我们所想要的，我们可以用-O选项来改变将文件保存为editplus.exe

D:\Hack stuff\wget>wget -O editplus.exe http://software-files-a.cnet.com/s/software/12/32/81/47/
epp331.exe?token=1329413178_4553efa847829f3ecef10c1bc256fcc0&lop=link&ptype=3001
&ontid=2352&siteId=4&edId=3&spi=537d5d5485f688682d82c481c4fb15a1&pid=12328147&ps
id=10018241&&fileName=epp331.exe
 

3、用Wget --limit-rate指定下载的速度

如下面这个例子限制速度为300k

D:\Hack stuff\wget>wget --limit-rate=300k http://downloads.sourceforge.net/project/boost/boost-doc
s/1.47.0/boost_1_47_pdf.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fboost%2F
&ts=1329379231&use_mirror=nchc
 

4、续传下载用Wget -c

当你在下载一个大文件时突然中断了那么这个选项就派上用场了

D:\Hack stuff\wget>wget -c http://downloads.sourceforge.net/project/boost/boost-doc
s/1.47.0/boost_1_47_pdf.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fboost%2F
&ts=1329379231&use_mirror=nchc
 

5、后台下载用wget -b

用此选项下载时只会初始化下载而不会显示相关信息

D:\Hack stuff\wget>wget -b http://downloads.sourceforge.net/project/boost/boost-
docs/1.47.0/boost_1_47_pdf.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fboost
%2F&ts=1329379231&use_mirror=nchc
Continuing in background, pid 6132.
Output will be written to `wget-log'.
下载以后会在wget目录下生产wget-log文件，用记事本打开可查看里面的内容如下所示

--2012-02-16 16:12:55--  http://downloads.sourceforge.net/project/boost/boost-docs/1.47.0/boost_1_47_pdf.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fboost%2F
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://nchc.dl.sourceforge.net/project/boost/boost-docs/1.47.0/boost_1_47_pdf.zip [following]
--2012-02-16 16:12:56--  http://nchc.dl.sourceforge.net/project/boost/boost-docs/1.47.0/boost_1_47_pdf.zip
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31421410 (30M) [application/zip]
Saving to: `boost_1_47_pdf.zip.4'

     0K .......... .......... .......... .......... ..........  0% 19.7K 25m51s
    50K .......... .......... .......... .......... ..........  0% 29.1K 21m40s
   100K .......... .......... .......... .......... ..........  0% 20.8K 22m35s
   150K .......... .......... .......... .......... ..........  0% 19.5K 23m26s
   200K .......... .......... .......... .......... ..........  0% 18.4K 24m13s
   250K .......... .......... .......... .......... ..........  0% 20.8K 24m13s
   300K .......... .......... .......... .......... ..........  1% 18.2K 24m41s
   350K .......... .......... .......... .......... ..........  1% 23.5K 24m16s
 

6、测试你要下载的地址用Wget --spider

wget --spider DOWNLOAD-URL
如果所给URL是正确的则会显示

Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/boost/boost-docs/1.47.0/boost_1_
47_pdf.zip [following]
Spider mode enabled. Check if remote file exists.
--2012-02-16 16:21:08--  http://ncu.dl.sourceforge.net/project/boost/boost-docs/
1.47.0/boost_1_47_pdf.zip
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31421410 (30M) [application/zip]
Remote file exists.
否则显示

Spider mode enabled. Check if remote file exists.
--2012-02-16 16:23:06--  http://downloads.sourceforge.net/project/boost/boost-do
cs/1.47.0/boost_1_47_pdf222.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fboos
t%2F
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
Remote file does not exist -- broken link!!!
 

7、增加重连次数用Wget -tries

在网络有问题的情况次选项尤其有用，默认是wget会重连20次以成功完成下载，我们可以把他增加为我们期待的次数

wget --tries=100 DOWNLOAD-URL

8、下载多个文件/URLS用wget -i

首先把所有要下载的文件或者URL存到一个记事本中，比如aa.txt，里面内容如下

URL1
URL2
URL3
URL4
接下来输入如下代码就可以批量下载了

wget -i aa.txt
 

9、下载一个完整的网站用wget -mirror

以下实现是你想完整的下载一个网站用于本地浏览

wget --mirror  -p --convert-links -P LOCAL-DIR WEBSITE-URL
--mirror:打开镜像选项

-p:下载所有用于显示给定网址所必须的文件

--convert-links：下载以后，转换链接用于本地显示

-P LOCAL_DIR：保存所有的文件或目录到指定的目录下

 

10、保存输出到日志文件而不是标准输出用wget -o

当你想要把信息保存到一个文件而不是在终端显示时用以下代码。

wget -o download.log DOWNLOAD-URL
 

11、当超过指定大小时终止下载用wget -Q

当文件已下载10M，此时你想停止下载可以使用下面的命令行

wget -Q10m -i FILE-WHICH-HAS-URLS
注意：此选项只能在下载多个文件时有用，当你下载一个文件时没用。

 

12、下载特定文件类型的文件用wget -r -A

你可以用此方法下载一下文件：

~从一个网站下载所有图片
~从一个网站下载所有视频

~从一个网站下载所有PDF文件

wget -r -A.pdf http://url-to-webpage-with-pdfs/
 

13、指定不下载某一类型的文件用wget --reject

你发现一个网站很有用，但是你不想下载上面的图片，因为太占流量，此时你可以用如下命令。

wget --reject=gif WEBSITE-TO-BE-DOWNLOADED

14、用wget实现FTP下载

匿名FTP下载用

wget ftp-url
有用户名和密码的FTP下载

wget --ftp-user=USERNAME --ftp-password=PASSWORD DOWNLOAD-URL
 

15、wget下载有的资源时必须用选项 --no-check-certificate，否则会提示没有认证不允许下载

wget --no-check-certificate URL