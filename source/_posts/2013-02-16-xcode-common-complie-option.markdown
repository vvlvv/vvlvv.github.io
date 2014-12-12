---
layout: post
title: "Xcode 常用编译选项设置"
date: 2013-02-16 11:39
comments: true
categories: xcode
---
用标准库连接

LINK_WITH_STANDARD_LIBRARIES = YES

如果激活此设置，那么编译器在链接过程中会自动使用通过标准库的链接器。

Info.plist 输出编码

INFOPLIST_OUTPUT_FORMAT = binary

指定Info.plist文件的输出编码（默认情况下，输出与输入的编码保持不变），这个输出编码能指定“binary”或者“XML”。

生成调试符号

GCC_GENERATE_DEBUGGING_SYMBOLS = NO

当启用的时候，详情等级能够通过build的'Level of Debug Symbols'设置去控制。

隐藏内联方法

GCC_INLINES_ARE_PRIVATE_EXTERN = YES

Objective－C GC

GCC_ENABLE_OBJC_GC = Unsupported

优化级别

GCC_OPTIMIZATION_LEVEL = Fastest, Smallest   [-OS]

* None: 不做优化使用这个设置，编译器的目标是减少编译成本，使调试产生预期的结果。
* Fast：优化编译将为大函数占用更多的时间和内存使用这个设置，编译器将尝试减少代码的大小和执行时间，不进行任何优化，需要大量编译时间。
* Faster：编译器执行几乎所有支持的优化，它不考虑空间和速度之间的平衡与“Fast”设置相比，该设置会增加编译时间和生成代码的性能。编译器不进行循环展开、内联函数和寄存器变量的重命名。
* Fastest：开启“Faster”支持的所有的优化，同时也开启内联函数和寄存器变量的重命名选项
* Fastest,smallest：优化代码大小这个设置启用“Faster”所有的优化，一般不增加代码大小，它还执行旨在减小代码大小的进一步优化。

C语言方言

GCC_C_LANGUAGE_STANDARD = C89

警告

检查Switch语句

GCC_WARN_CHECK_SWITCH_STATEMENTS = YES

隐藏局部变量

GCC_WARN_SHADOW = YES

隐式转换成32位的类型

GCC_WARN_64_TO_32_BIT_CONVERSION = YES

未完成的Objective－C协议

GCC_WARN_ALLOW_INCOMPLETE_PROTOCOL = YES

抑制所有的警告

GCC_WARN_INHIBIT_ALL_WARNINGS = NO

初始化时没有完整的括号

GCC_WARN_INITIALIZER_NOT_FULLY_BRACKETED = YES

例子（a没有完全的括号，b有）：

```
int a[ 2 ][ 2 ] = { 0, 1, 2, 3 };   
int b[ 2 ][ 2 ] = { { 0, 1 }, { 2, 3 } }; 
```

不匹配的返回类型

GCC_WARN_ABOUT_RETURN_TYPE = YES

缺少括号

GCC_WARN_MISSING_PARENTHESES = YES

例子：

```
{  
    if( a )  
        if( b )  
            foo();  
        else  
            bar();  
} 
```
```
{  
    if( a )  
    {  
        if( b )  
            foo();  
        else  
            bar();  
    }  
} 
```

在结构体初始化时缺少字段

GCC_WARN_ABOUT_MISSING_FIELD_INITIALIZERS = YES

缺少函数原型

GCC_WARN_ABOUT_MISSING_PROTOTYPES = YES

在文件结尾缺少新行

GCC_WARN_ABOUT_MISSING_NEWLINE = YES

选择了多个定义的类型(@Selector)

GCC_WARN_MULTIPLE_DEFINITION_TYPES_FOR_SELECTOR = NO

严格的Selector匹配

GCC_WARN_STRICT_SELECTOR_MATCH = YES

把缺少函数原型当作错误

GCC_TREAT_IMPLICIT_FUNCTION_DECLARATIONS_AS_ERRORS = YES

把所有的警告当作错误

GCC_TREAT_WARNINGS_AS_ERRORS = YES

未定义的Selector

GCC_WARN_UNDECLARED_SELECTOR = YES

未初始化的自动变量

GCC_WARN_UNINITIALIZED_AUTOS = YES

未知的Pragma指令

GCC_WARN_UNKNOWN_PRAGMAS = YES

未使用的函数

GCC_WARN_UNUSED_FUNCTION = YES

未使用的标签

GCC_WARN_UNUSED_LABEL = YES

未使用的参数

GCC_WARN_UNUSED_PARAMETER = YES

未使用的值

GCC_WARN_UNUSED_VALUE = YES

当一个语句计算的结果显式的未使用的时候发出警告

未使用的变量

GCC_WARN_UNUSED_VARIABLE = YES

警告－所有过时的函数

GCC_WARN_ABOUT_DEPRECATED_FUNCTIONS = YES

offsetof宏未定义使用的警告

GCC_WARN_ABOUT_INVALID_OFFSETOF_MACRO = YES