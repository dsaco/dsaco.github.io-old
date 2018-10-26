---
layout: post
title:  "Javascript中的正则表达式"
date:   2018-10-25 13:34:00 +0800
tags: Javascript RegExp 正则
---

人生自古谁无死 留取丹青照汗青

###### 删除字符串str中的span标签
```
str.replace(/<\/?span[^>]*>/g,'');
```
##### 判断是否为手机号码
```
phoneNumber.match(/^1\d{10}$/);
```
##### 判断是否由中文组成
```
/^[\u4E00-\u9FA5]+$/.test('中文');
```
##### 判断是否为字母、数字、下划线组成
```
/^\w+$/.test(str);
```