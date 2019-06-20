---
layout: post
title:  "React-Native错误汇总"
date:   2019-03-25 11:20:00 +0800
tags: React-Native Errors
---

- 启动开发异常 **Command failed: gradlew.bat installDebug**

在android/gradle.properties添加

```
sdk.dir = C:\\Users\\Administrator\\AppData\\Local\\Android\\Sdk
```

- 打包报异常 unable to process incoming event 'ProcessComplete' <ProgressCompleteEvent>

可以用``gradlew.bat assembleRelease --console plain``代替 ``gradlew assembleRelease``

- Ios打包异常 (Realm 在Xcode 10.2.1)
**enumeration value 'kJSTypeSymbol'**

[Issue](https://github.com/realm/realm-js/issues/2305#issuecomment-476561324)

