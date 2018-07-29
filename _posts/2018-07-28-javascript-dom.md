---
layout: post
title:  "HTML DOM 元素对象"
date:   2018-07-28 22:45:55 +0800
tags: javascript api
cover: "/assets/img/home-bg.jpg"
---


addEventListener()方法用于向指定元素添加事件句柄。

``element.addEventListener(event,function,useCapture)``

useCapture 可选。布尔值，指定事件是否字捕获或冒泡阶段执行。

appendChild()方法可向节点的子节点列表的末尾添加新的子节点。

``element.appendChild(node)``

cloneNode()方法可创建指定的节点的精确拷贝，拷贝所有的属性和值。
``element.cloneNode(deep:boolean)`` : element (true复制子节点)

compareDocumentPosition()方法按照文档顺序，比较当前节点与指定节点的文档位置。

``ele1.compareDocumentPosition(ele2)`` : number

1: 没有关系；2:ele1在ele2后；4:ele1在ele2前；8:ele1在ele2内；16:ele2在ele1内；32:没有关系或在同一元素的两个属性。可以组合返回 20: ele2在ele1内并且ele1在ele2前。

## 属性
attributes 获取元素属性的集合

``element.attributes``

childNodes 获取元素的子节点集合

``element.childNodes``

className 获取元素的class属性

``element.className`` : string

classList 获取元素的类名

``element.classList`` : 类名列表

在元素中添加一个或多个类名。

``element.classList.add(class1,class2)``

判断指定类名是否存在。

``element.classList.contains(class)`` : boolean

移除元素中一个或多个类名。

``element.classList.remove(class1,class2)``

在元素中切换类名。

``element.classList.toggle(class)`` ：boolean （添加 true，移除false）
