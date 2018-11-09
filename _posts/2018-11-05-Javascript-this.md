---
layout: post
title:  "Javascript中的this"
date:   2018-11-05 17:19:00 +0800
tags: Javascript this
---


> 当一个函数被调用时，拥有它的object会作为this传入。在global下，就是window or global，其他时候就是相应的object。
> 函数里面嵌套的函数属于哪个object的，如果没有就是window。
> 全局作用域下 this指向window `"use strict;"`严格模式下为undefined