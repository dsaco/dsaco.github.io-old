---
layout: post
title:  "React-Native错误汇总"
date:   2019-03-25 11:20:00 +0800
tags: React-Native error
---

- 启动项目 gradle下载缓慢 

手动下载gradle并且配置android/gradle/wrapper/gradle-wrapper.properties 
```
distributionUrl=file:///D:/Android/my-gradle/gradle-5.4.1-all.zip
```

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

- 解决升级到Xcode10，react native项目运行报错问题
```
Xcode 10: Build input file double-conversion cannot be found
error: Build input file cannot be found: '../node_modules/react-native/third-party/double-conversion-1.1.6/src/strtod.cc'
configure: error: in `../node_modules/react-native/third-party/glog-0.3.4'
```

1. cd node_modules/react-native/scripts && ./ios-install-third-party.sh && cd ../../../
2. cd node_modules/react-native/third-party/glog-0.3.4/ && ../../scripts/ios-configure-glog.sh && cd ../../../../

- Ios打包异常 main.jsbundle does not exist

修改 Build Phases / Bundle React Native code and images

export NODE_BINARY= /usr/local/bin/node