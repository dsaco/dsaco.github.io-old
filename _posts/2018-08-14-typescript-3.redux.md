---
layout: post
title:  "Typescript redux配置"
date:   2018-08-14 22:45:00 +0800
tags: typescript react react-redux react-router redux-saga webpack tslint
---

最近一直在想怎么结合redux、saga写项目，如果按照之前的写法，那就是三个文件夹：actions，reducers，sagas。但是这么写很繁琐，虽然dva封装的很好，但是问题也是它封装的太好了，emmm...，让我再想想。。。

{% highlight js %}
cnpm i -S redux react-redux redux-saga redux-logger @types/react-redux @types/redux-logger
{% endhighlight %}
