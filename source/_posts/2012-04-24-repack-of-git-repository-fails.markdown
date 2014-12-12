---
layout: post
title: "Repack of Git repository fails"
date: 2012-04-24 11:00
comments: true
categories: git
---
### question
I have a git repository residing on a server with limited memory. When I try to clone an existing repository from the server I get the following error

```
Cloning into 'carRecognition'...
remote: Counting objects: 3012, done.
error: git upload-pack: git-pack-objects died with error.
fatal: git upload-pack: aborting due to possible repository corruption on the remote side.
remote: aborting due to possible repository corruption on the remote side.
fatal: early EOF
fatal: index-pack failed
```

### solution
Your solution has got you a working copy locally and remotely, but will cause problems again when the remote repository decides to repack itself again. Fortunately, you can set config options that will reduce the amount of memory needed for repacking in both repositories -- these essentially make the command line parameters that you added into the default options when repacking. So, you should log in to the remote, change into the repository and do:

```
git config pack.windowMemory 10m
git config pack.packSizeLimit 20m
```

You may want to do the same on your local repository. (Incidentally I guess that either your repository is very large or these are machines with little memory - these values seem very low to me.)

For what it's worth, when getting malloc failures on repacking very large repositories in the past, I've also changed the values of core.packedgitwindowsize, core.packedgitlimit, core.deltacachesize, pack.deltacachesize, pack.window and pack.threads but it sounds as if you don't need any further options :)

> 本该淡淡然~~~