---
layout: post
title:  "Python基础"
date:   2019-07-04 13:00 +0800
tags: Python

---

### 字符串

> 大写首字母

{% highlight python %}
name = "peter wang"
print(name.title())
{% endhighlight %}

> 大小写字母

{% highlight python %}
name = "Peter Wang"
print(name.upper())
print(name.lower())
{% endhighlight %}

> 删除空白字符

{% highlight python %}
name = "  Peter Wang  "
print(name.strip())
print(name.rstrip())
print(name.lstrip())
{% endhighlight %}

### 数字

{% highlight python %}
# 乘方运算
total = 3 ** 2
total = 9
total = 3 ** 3
total = 27

{% endhighlight %}