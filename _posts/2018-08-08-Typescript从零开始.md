---
layout: post
title:  "Typescript从零开始"
date:   2018-08-08 22:26:00 +0800
tags: Typescript React
---

跟着[官网](https://www.tslang.cn/docs/handbook/react-&-webpack.html)的例子，我们现在已经把环境搭建起来了
从前我们习惯性的写：
{% highlight js %}
import React,{ Component } from 'react';
{% endhighlight%}
官网上给的例子是：
{% highlight js %}
import * as React from 'react';
{% endhighlight%}
当我们引入不是用ES6编写的React时，它没有使用默认的导出，（has no default export），如果想继续使用ES6风格的代码可以添加``allowSyntheticDefaultImports:true``配置进``tsconfig.json``

---
接下来你有可能会报一个错``Cannot read property 'createElement' of undefined`` [issue](https://github.com/eggjs/egg/issues/2409)

添加``esModuleInterop:true``配置，此配置默认开启``allowSyntheticDefaultImports``，区分命名空间导入和默认导入的行为，使得模块的导入行为更符合ES6模块的规范，同时与Babel的转译行为保持一致：

命名空间的导入方式：
{% highlight js %}
import * as React from 'react';
{% endhighlight%}
默认导入的导入方式：
{% highlight js %}
import React from 'react';
{% endhighlight%}
开启 esModuleInterop 编译选项后，当使用命名空间的导入方式时，导入对象不可调用/不可实例化。当使用默认导入的导入方式时，导入对象应当可调用/可实例化。

开启 esModuleInterop 前：
{% highlight js %}
import * as express from 'express';
express()
{% endhighlight%}
开启 esModuleInterop 后：
{% highlight js %}
import express from 'express';
express()
{% endhighlight%}
