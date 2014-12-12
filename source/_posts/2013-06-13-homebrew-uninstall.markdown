---
layout: post
title: "Homebrew uninstall"
date: 2013-06-13 13:15
comments: true
categories: mac
---
```
cd `brew –prefix`
rm -rf Cellar
brew prune
rm -rf Library .git .gitignore bin/brew README.md share/man/man1/brew
rm -rf ~/Library/Caches/Homebrew
```