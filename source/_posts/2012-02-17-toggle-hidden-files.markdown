---
layout: post
title: "如何制作Snow Leopard切换隐藏文件显示状态的快捷键(转帖)"
date: 2012-02-17 16:23
comments: true
categories: mac
---
出处 (<http://lucifr.com/>)

用上Mac OS X 10.6 Snow Leopard (雪豹）的人们很快就发现在打开或是保存文件的对话框中(比如你可以在Firefox中找个图片然后另存为这时就会打开一个对话框）可以快捷地通过Command+Shift+.（句号）来切换隐藏文件的显示状态。但是在一般状态下的Finder当中却不能这么干，这无疑是反界面友好性的，于是很快有人想出了办法，让这种切换在Finder中也能实现。

具体步骤如下：

* 运行Automator，就是应用程序中抱着钢管的小机器人。它会提示你选择模板，点下“服务”然后按“选取”。
* 在最左边栏的“资源库”中选择“实用工具”。
* 将第二栏中的“运行Shell脚本”拖到右上的面板里。
* 这时右上面板中会出现“运行Shell脚本”的对话框。先把“位置”右侧的现在显示为“任何应用程序”的下拉菜单改为“Finder”，这样就保证了这个脚本只会在“Finder”里运行。
* 把“服务接收选定的”右侧的默认显示为“文本”的下拉菜单改为“没有输入”。这一步一定要在上一步之后做，否则位置里就不能选“Finder”了。
* 拷贝下面的文本并将之粘贴到“运行Shell脚本”的文本区域中：

```
STATUS=`defaults read com.apple.finder AppleShowAllFiles` 
if [ $STATUS == YES ]; 
then 
defaults write com.apple.finder AppleShowAllFiles NO 
else 
defaults write com.apple.finder AppleShowAllFiles YES 
fi 
killall Finder 
```

* 到这脚本做好了，选择“文件”–>“存储”，命名为“Toggle Hidden Files”或是其它的英文名并存储。这时你就可以在Finder的菜单“服务”里看到这个“Toggle Hidden Files”脚本了。这时点击它已经可以起作用，接下来我们还要加上快捷键。
* 打开“系统偏好设置”–>“键盘”–>“键盘快捷键”，左侧面板中选择“服务”。
* 在右侧面板的滚动到最下面就可以看到我们刚才制作的“Toggle Hidden Files”。选择它，然后双击右侧的空白处，这时就可以自定义快捷键了，建议使用“Shift+Command+.”（.为句号），与打开或是保存文件的对话框中的快捷键保持一致。完成后关闭“系统偏好设置”。

这时在Finder中按下Shift+Command+.就可以切换隐藏文件的显示与否了。按了之后Finder会自动关闭并重启。

---
P.S. 这个脚本目前似乎还有待完善，有时候Finder不能正常启动，有时启动了却不在Dock中显示，对于前一种情况，手动启动就行了，后一种情况则需要用“活动监视器”杀掉Finder的进程，然后手动重启。

> 本该淡淡然~~~