---
layout: post
title: "上传appstore通过命令行"
date: 2013-06-27 13:41
comments: true
categories: ios
---

>
未验证（先记录下来，后续研究）[来源](http://stackoverflow.com/questions/11888122/how-to-upload-an-ios-app-to-the-app-store-via-command-line)

* Make sure you have an application in "waiting to upload" state.

* Create a new keychain Item Named: Xcode:itunesconnect.apple.com provide your credentials to itunes connect.

* From the command line: 

```
xcrun -sdk iphoneos Validation -online -upload -verbose "path to ipa"
```



```
This is perfect. I've lots of clients and customers. I want to upload apps on behalf of my clients/customers, how can I create respective key chain items and provide them during "xcrun" command? – Satyam svv Dec 1 '12 at 2:28

you can create a ad-hoc key before running xcrun and discart it after the upload is finished security add-generic-password -s Xcode:itunesconnect.apple.com -a LOGIN -w PASSWORD -U xcrun -sdk iphoneos Validation -online -upload -verbose "path to ipa" security delete-generic-password -s Xcode:itunesconnect.apple.com -a LOGIN
```