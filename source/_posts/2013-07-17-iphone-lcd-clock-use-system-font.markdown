---
layout: post
title: "iphone lcd clock use system font"
date: 2013-07-17 22:16
comments: true
categories: ios
---
iPhone 默认的液晶时钟效果很是经典，如果您想在自己的应用里显示该时钟，可以用以下代码

```
[UIFont fontWithName:@"DBLCDTempBlack" size:58]
```
* 此外，类似 DBLCDTempBlack 的可用字体列表：

```
Family name: AppleGothic
Font name: AppleGothic
Family name: Hiragino Kaku Gothic ProN
Font name: HiraKakuProN-W6
Font name: HiraKakuProN-W3
Family name: Arial Unicode MS
Font name: ArialUnicodeMS
Family name: Heiti K
Font name: STHeitiK-Medium
Font name: STHeitiK-Light
Family name: DB LCD Temp
Font name: DBLCDTempBlack
Family name: Helvetica
Font name: Helvetica-Oblique
Font name: Helvetica-BoldOblique
Font name: Helvetica
Font name: Helvetica-Bold
Family name: Marker Felt
Font name: MarkerFelt-Thin
Family name: Times New Roman
Font name: TimesNewRomanPSMT
Font name: TimesNewRomanPS-BoldMT
Font name: TimesNewRomanPS-BoldItalicMT
Font name: TimesNewRomanPS-ItalicMT
Family name: Verdana
Font name: Verdana-Bold
Font name: Verdana-BoldItalic
Font name: Verdana
Font name: Verdana-Italic
Family name: Georgia
Font name: Georgia-Bold
Font name: Georgia
Font name: Georgia-BoldItalic
Font name: Georgia-Italic
Family name: Arial Rounded MT Bold
Font name: ArialRoundedMTBold
Family name: Trebuchet MS
Font name: TrebuchetMS-Italic
Font name: TrebuchetMS
Font name: Trebuchet-BoldItalic
Font name: TrebuchetMS-Bold
Family name: Heiti TC
Font name: STHeitiTC-Light
Font name: STHeitiTC-Medium
Family name: Geeza Pro
Font name: GeezaPro-Bold
Font name: GeezaPro
Family name: Courier
Font name: Courier
Font name: Courier-BoldOblique
Font name: Courier-Oblique
Font name: Courier-Bold
Family name: Arial
Font name: ArialMT
Font name: Arial-BoldMT
Font name: Arial-BoldItalicMT
Font name: Arial-ItalicMT
Family name: Heiti J
Font name: STHeitiJ-Medium
Font name: STHeitiJ-Light
Family name: Arial Hebrew
Font name: ArialHebrew
Font name: ArialHebrew-Bold
Family name: Courier New
Font name: CourierNewPS-BoldMT
Font name: CourierNewPS-ItalicMT
Font name: CourierNewPS-BoldItalicMT
Font name: CourierNewPSMT
Family name: Zapfino
Font name: Zapfino
Family name: American Typewriter
Font name: AmericanTypewriter
Font name: AmericanTypewriter-Bold
Family name: Heiti SC
Font name: STHeitiSC-Medium
Font name: STHeitiSC-Light
Family name: Helvetica Neue
Font name: HelveticaNeue
Font name: HelveticaNeue-Bold
Family name: Thonburi
Font name: Thonburi-Bold
Font name: Thonburi
```