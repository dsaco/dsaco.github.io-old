---
layout: post
title:  "react-native"
date:   2018-10-24 15:21:00 +0800
tags: React React-Native
---

### 安装
克隆完项目后  ``npm i``总是失败 所以打算用yarn安装

[windows安装yarn](https://yarn.bootcss.com/docs/install/#windows-stable)

msi安装地址是404

Chocolatey安装

```
choco install yarn
yarn --version
```
yarn安装失败
失败原因 需要 4-9版本的node

安装nvm
```
nvm install 8.12.0
nvm use 8.12.0
```

配置 ANDROID_HOME 环境变量
path %ANDROID_HOME%

错误：peer not authenticated
试着修改``<android-project-path>/gradle/wrapper/gradle-wrapper.properties``中的https改为http
```
distributionUrl=http\://services.gradle.org/distributions/gradle-2.4-all.zip
```
错误：failed to find target with hash string 'android-25' in : xxxx
在android-studio中安装 android-25

错误
```
> Could not resolve all dependencies for configuration ':classpath'.
      > Could not resolve com.android.tools.build:gradle:1.3.1.
        Required by:
            :react_native_helloworld:unspecified
         > Could not resolve com.android.tools.build:gradle:1.3.1.
            > Could not get resource 'https://jcenter.bintray.com/com/android/tools/build/gradle/1.3.1/gradle-1.3.1.pom'.
               > Could not HEAD 'https://jcenter.bintray.com/com/android/tools/build/gradle/1.3.1/gradle-1.3.1.pom'.
                  > peer not authenticated
```
replace jcenter() with jcenter { url "http://jcenter.bintray.com/"} in build.gradle

错误 Getting Execution failed for task ':app:packageAllDebugClassesForMultiDex'. > java.util.zip.ZipException: duplicate entry: android/support/v7/appcompat/R$anim.class
进入项目目录 cd android && gradlew clean
