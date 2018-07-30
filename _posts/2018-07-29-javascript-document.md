---
layout: post
title:  "HTML document对象"
date:   2018-07-29 22:45:55 +0800
tags: javascript api
cover: "/assets/img/home-bg.jpg"
---
#### 属性
> ``.activeElement`` 返回当前获取焦点的元素

> ``.anchors`` 返回对文档中所有Anchor对象(锚点)的引用

> ``.baseURI`` 返回文档的绝对基础URI

> ``.body`` 返回文档的body元素

> ``.cookie`` **设置或返回**与当前文档有关的所有cookie

> ``.doctype`` 返回与文档相关的文档类型声明(DTD)

> ``.documentElement`` 返回文档的根节点

> ``.domain`` 返回当前文档的域名

> ``.forms`` 返回对文档中所有Form对象引用

> ``.images`` 返回对文档中所有Image对象引用

> ``.inputEncoding`` 返回用于文档的编码方式(在解析时)

> ``.links`` 返回对文档中所有Area和Link对象引用

> ``.readyState`` 返回文档状态

> ``.scripts`` 返回页面中所有脚本的集合

> ``.title`` 返回当前文档的标题

> ``.URL`` 返回文档完成的URL

#### 方法
> ``.addEventListener()`` 向文档添加句柄

> ``.createAttribute()`` 创建一个属性节点

> ``.createComment()`` 创建注释节点

> ``.createElement()`` 创建元素节点

> ``.createTextNode()`` 创建文本节点

> ``.getElementsByClassName()`` 返回文档中指定类名的元素集合

> ``.getElementById()`` 返回对拥有指定id的第一个对象的引用

> ``.getElementsByName()`` 返回带有指定名称的对象集合(例:表单的name)

> ``.normalize()`` 删除空文本节点,并连接相邻节点

> ``.open()`` 打开一个流,收集来自任何document.write()或document.writeIn()方法的输出

> ``.querySelector()`` 返回文档中匹配指定的css选择器的第一个元素

> ``.querySelectorAll()`` 返回文档中匹配指定的css选择器的元素集合

> ``.removeEventListener()`` 移除文档中的事件句柄

> ``.write()`` 向文档写HTML表达式或javascript代码

> ``.writeIn()`` 等同于write(),不同的是在每个表达式之后写一个换行符
