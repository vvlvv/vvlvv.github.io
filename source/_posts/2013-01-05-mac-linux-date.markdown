---
layout: post
title: "mac linux date"
date: 2013-01-05 11:39
comments: true
categories: terminal
---
###Mac和Linux下，分别如何用date命令表示明天
#####Linux 平台，用date表示明天
    
    date -d "tomorrow"

类似的有：

    date -d "yesterday"    # 顯示昨天的時間
    date -d "tomorrow"     # 顯示明天的時間
    date -d "1 hour"       # 顯示一小時後的時間
    date -d "2 day ago"    # 顯示二天前的時間
    date -d "3 month ago"  # 顯示三個月前的時間
    date -d "2 year"       # 顯示二年後的時間
    date -d "last friday"  # 顯示上個星期五的時間
    date -d "next week"    # 顯示下週的時間
    date -d "next month"   # 顯示下個月的時間
    date -d "fortnight"    # 顯示二週後的時間
    date -d "7/1 3 week"   # 顯示 7/1 起算的第三週


#####Mac 平台，用date表示明天

    #Mac下的date能接受-r选项，-r 接受多少秒作为其参数
    #86400 = 60 * 60 * 24 (s) = 24 (h)
    date -r $(expr $(date '+%s') + 86400)
    
> 本该淡淡然~~~