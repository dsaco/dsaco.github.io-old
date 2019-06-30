---
layout: post
title:  "Python网络请求"
date:   2019-06-18 21:32 +0800
tags: Python requests
desc: "
    晓看天色暮看云, 行也思君, 坐也思君 \n
    昼赏微云夜观星, 醒亦念卿, 寐亦念卿 \n
    春临百花冬见雪, 冷也是你, 暖也是你 \n
    海上明月眼前人, 远亦怀若, 近亦怀若
"
---

```
pip install requests
```

{% highlight python %}
import requests

response =  requests.get('http://admin.ds-or.com/test')

print(response)

if response.ok:
    print('ok')
else:
    print('not ok')
{% endhighlight %}
