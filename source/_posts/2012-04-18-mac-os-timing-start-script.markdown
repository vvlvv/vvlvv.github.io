---
layout: post
title: "Mac OS timing start script"
date: 2012-04-18 16:54
comments: true
categories: mac
---

前面的文章提到过[Linux Crontab](http://livv.github.com/blog/2012/03/01/linux-crontab/)，用法几乎一样。

```
sudo crontab -e//回车后输入密码
//进入VI编辑，输入
* * * * * say hello//这个地方可以放脚本的路径
保存即可。
这样每分钟都会听到hello了
```
```
五个星星表示
minute — 分钟，从 0 到 59 之间的任何整数 
hour — 小时，从 0 到 23 之间的任何整数 
day — 日期，从 1 到 31 之间的任何整数（如果指定了月份，必须是该月份的有效日期） 
month — 月份，从 1 到 12 之间的任何整数（或使用月份的英文简写如 jan、feb 等等） 
dayofweek — 星期，从 0 到 7 之间的任何整数，这里的 0 或 7 代表星期日（或使用星期的英文简写如 sun、mon 等等）
```
```
crontab -l显示目前所有的任务
crontab -r删除所有的任务
crontab -e编辑任务
```
***
* 以上方法好像不能调用本地sh脚本，改用`~/Library/LaunchAgents/vv.redmine.bak.plist` 这样每天12:30调用`/Users/wei/architect/redmine_bak/redmine_bak.sh`

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
        <key>Label</key>
        <string>vv.redmine.bak</string>
        <key>ProgramArguments</key>
        <array>
                <string>/Users/wei/architect/redmine_bak/redmine_bak.sh</string>
        </array>
        <key>StartCalendarInterval</key>
        <array>
                <dict>
                        <key>Minute</key>
                        <integer>30</integer>
                </dict>
                <dict>
                        <key>Hour</key>
                        <integer>12</integer>
                </dict>
        </array>
</dict>
</plist>
```

> 本该淡淡然~~~