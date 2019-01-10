---
layout: post
title:  "Javascript冷知识"
date:   2018-11-13 10:55:00 +0800
tags: Javascript API
---

```
(123456789).toLocaleString('en-US')  // 1,234,567,890
new Intl.NumberFormat().format(1234567890) // 1,234,567,890
123456789..toLocaleString('zh-hans-CN-u-nu-hanidec') // "一二三,四五六,七八九"
123456789..toLocaleString('zh-hans-CN-u-nu-hanidec',{useGrouping:true}) // "一二三,四五六,七八九"
123456789..toLocaleString('zh-hans-CN-u-nu-hanidec',{useGrouping:false}) // "一二三四五六七八九"
new Date().toLocaleString('zh-hans-CN-u-nu-hanidec') // "二〇一八/一一/一三 上午一一:〇〇:五四"
```

判断 otherNode是不是node的子节点
```
node.contains( otherNode )
```

表单label不同字数对齐方法
```
.text {
    text-align:justify;
    text-justify:distribute-all-lines;/*ie6-8*/
    text-align-last:justify;/* ie9*/
    -moz-text-align-last:justify;/*ff*/
    -webkit-text-align-last:justify;/*chrome 20+*/
}
@media screen and (-webkit-min-device-pixel-ratio:0){/* chrome*/
    .text:after{
        content:".";
        display: inline-block;
        width:100%;
        overflow:hidden;
        height:0;
    }
}
```