---
layout: post
title: "launchctl manual"
date: 2013-03-12 13:54
comments: true
categories: mac
---
###相关目录

* /System/Library/LaunchDaemons 操作系统，用户登录前生效，以 root 身份执行任务
* /System/Library/LaunchAgents 操作系统，用户登录后生效，以 root 身份执行任务
* /Library/LaunchDaemons 系统管理员，用户登录前生效，以 root 身份执行任务
* /Library/LaunchAgents 系统管理员，用户登录后生效，以 root 身份执行任务
* ~/Library/LaunchAgents 当前用户，用户登录后生效，以当前登录用户身份执行任务
使任务生效

将 plist 文件按需要放置在上文的相关目录中
###使任务生效
```
launchctl load <plist path>
```
执行上述操作后任务会立即生效，且重启系统后也会自动生效。如果 plist 没有放在指定的目录，重启系统后不会再生效。

如果 plist 存在 Key Disabled，且其值为 true，launchctl load 会提示 nothing found to load，系统启动时也不会自动生效人物，如果要手动强制启动，忽略 Disabled 为 true 带来的影响，传递 -wF 参数给 launchctl 即可。

###使任务失效
```
launchctl unload <plist path>
```
将相关 plist 文件从原有目录中移除
执行上述操作后，任务会立即失效，plist 文件不会被移除，但是如果不将其从相关目录移走的话，重启系统后任务仍然会自动生效。