---
layout: post
title:  "Javascript 事件"
date:   2018-11-06 11:20:00 +0800
tags: Javascript event
---

床前明月光 疑是地上霜

```
<ul>
    <li></li>
    <li></li>
    <li></li>
</ul>
```
比起循环每个li并绑定点击事件，不如
{% highlight js %}
const ul = document.querySelector('ul');
ul.onclick = function(e) {
    let e = e || window.event;
    let target = e.target || e.srcElement;
    if (target.nodeName.toLowerCase() === 'li') {
        console.log(target.innerHTML);
    }
}
{% endhighlight %}
```
const ul = document.querySelector('ul');
ul.onclick = function(e) {
    let e = e || window.event;
    let target = e.target || e.srcElement;
    if (target.nodeName.toLowerCase() === 'li') {
        console.log(target.innerHTML);
    }
}
```
优点：只添加一个监听事件，节省了内存；新加入li的时候我们也不用为它单独添加监听事件；在页面中添加事件处理程序所需的时候更少，因为我们只需要为一个DOM元素添加事件处理程序。