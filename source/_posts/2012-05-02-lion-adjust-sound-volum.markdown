---
layout: post
title: "Lion下精确调整音量"
date: 2012-05-02 13:36
comments: true
categories: mac
---

升级到Lion后一直在忍受着很大的音量，戴着入耳一格音量也觉得很大，找了两句applescript，写成了一个符合我使用习惯的脚本，这下可以精确地把音量调整为舒适的大小了：

```
#!/usr/bin/osascript

on usage()
    set _usage to "Usage: adjust-volume number\n"
    set _usage to _usage & "For example:\n"
    set _usage to _usage & "  adjust-volume 2\t - increase volume by 2\n"
    set _usage to _usage & "  adjust-volume -2\t - decrease volume by 2"
    return _usage
end usage

on run argv
    if (count argv) < 1 then
        return usage()
    end if

    set currentVolume to output volume of (get volume settings)
    set volume output volume (currentVolume + (item 1 of argv))
    return "Current volume level: " & output volume of (get volume settings)
end run
```

使用方法：

Usage: adjust-volume number

For example:

```
 adjust-volume 2	 - increase volume by 2
 adjust-volume -2	 - decrease volume by 2
```

> 本该淡淡然~~~