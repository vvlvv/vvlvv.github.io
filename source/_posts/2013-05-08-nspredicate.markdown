---
layout: post
title: "NSPredicate 的用法"
date: 2013-05-08 09:22
comments: true
categories: ios
---
一般来说这种情况还是蛮多的，比如你从文件中读入了一个array1，然后想把程序中的一个array2中符合array1中内容的元素过滤出来。
正 常傻瓜一点就是两个for循环，一个一个进行比较，这样效率不高，而且代码也不好看。
其实一个循环或者无需循环就可以搞定了，那就需要用搞 NSPredicate这个类了～膜拜此类～
#####例子一，一个循环
```
NSArray *arrayFilter = [NSArray arrayWithObjects:@"pict", @"blackrain", @"ip", nil];
NSArray *arrayContents = [NSArray arrayWithObjects:@"I am a picture.", @"I am a guy", @"I am gagaga", @"ipad", @"iphone", nil];
```

我想过滤arrayContents的话只要循环 arrayFilter就好了

```
int i = 0, count = [arrayFilter count];
for(i = 0; i < count; i ++)
{
NSString *arrayItem = (NSString *)[arrayFilter objectAtIndex:i];
NSPredicate *filterPredicate = [[NSPredicate predicateWithFormat:@"SELF CONTAINS %@", arrayItem];
NSLog(@"Filtered array with filter %@, %@", arrayItem, [arrayContents filteredArrayUsingPredicate:filterPredicate]);
}
```
当然以上代码中arrayContent最好用mutable 的，这样就可以直接filter了，NSArray是不可修改的。

#####例子二，无需循环
```
NSArray *arrayFilter = [NSArray arrayWithObjects:@"abc1", @"abc2", nil];
NSArray *arrayContent = [NSArray arrayWithObjects:@"a1", @"abc1", @"abc4", @"abc2", nil];
NSPredicate *thePredicate = [NSPredicate predicateWithFormat:@"NOT (SELF in %@)", arrayFilter];
[arrayContent filterUsingPredicate:thePredicate];
```

这样arrayContent过滤出来的就是不包含 arrayFilter中的所有item了。

#####生成文件路径下文件集合列表
```
NSFileManager *fileManager = [NSFileManager defaultManager];
NSString *defaultPath = [[NSBundle mainBundle] resourcePath];
NSError *error;
NSArray *directoryContents = [fileManager contentsOfDirectoryAtPath:defaultPath error:&error]
```

`match的用法`

* 简单比较
   
```
NSString *match = @"imagexyz-999.png";
NSPredicate *predicate = [NSPredicate predicateWithFormat:@"SELF == %@", match];
NSArray *results = [directoryContents filteredArrayUsingPredicate:predicate];﻿
```

* match里like的用法（类似Sql中的用法）

```
NSString *match = @"imagexyz*.png";
NSPredicate *predicate = [NSPredicate predicateWithFormat:@"SELF like %@", match];
NSArray *results = [directoryContents filteredArrayUsingPredicate:predicate];﻿
```
* 大小写比较
  
［c］表示忽略大小写，［d］表示忽略重音，可以在一起使用，如下：

```
NSString *match = @"imagexyz*.png";
NSPredicate *predicate = [NSPredicate predicateWithFormat:@"SELF like[cd] %@", match];
NSArray *results = [directoryContents filteredArrayUsingPredicate:predicate];﻿
```

* 使用正则 

```
NSString *match = @"imagexyz-\\d{3}\\.png";  //imagexyz－123.png
NSPredicate *predicate = [NSPredicate predicateWithFormat:@"SELF matches %@", match];
NSArray *results = [directoryContents filteredArrayUsingPredicate:predicate];﻿
```

#####总结：
1. 当使用聚合类的操作符时是可以不需要循环的
2. 当使用单个比较类的操作符时可以一个循环来搞定

PS，例子 一中尝试使用[@"SELF CONTAINS %@", arrayFilter] 来过滤会挂调，因为CONTAINS时字符串比较操作符，不是集合操作符。