---
layout: post
title:  "javascript中Array的方法"
date:   2018-08-02 23:53:00 +0800
tags: javascript api array
cover: "/assets/img/home-bg.jpg"
---
以下会用到的变量：
{% highlight js %}
const fruits = ['apple','banana']
const names = ['tom','peter']
const numbers = [1,2,3,4,5]
{% endhighlight %}

#### concat
连接两个或更多的数组，并返回结果。
{% highlight js %}
// array.concat(array1,array2,...,arrayX) 参数可以是数组，也可以是具体值
fruits.concat('pear',['orange']) => ['apple','banana','pear','orange']
{% endhighlight %}
#### copyWithin
从数组的指定位置拷贝元素到数组的另一个指定位置中。**操作原数组**
{% highlight js %}
// array.copyWithin(target,start,end)
numbers.copyWithin(2,1,3)
numbers => [1,2,2,3,5]
{% endhighlight %}
#### entries
返回数组的可迭代对象。
{% highlight js %}
const iterable = fruits.entries()
iterable.next() => {done:false,value:[0,'apple']}
iterable.next() => {done:false,value:[1,'banana']}
iterable.next() => {done:true,value:undefined}
{% endhighlight %}
#### every
检测数值元素的每个元素是否都符合条件，如果数组中检测到有一个元素不满足，则整个表达式返回 false ，且剩余的元素不会再进行检测。
如果所有元素都满足条件，则返回 true。
{% highlight js %}
numbers.every((num) => num > 3) => false
{% endhighlight %}
#### fill
使用一个固定值来填充数组。**操作原数组**
{% highlight js %}
// array.fill(value, start, end) start开始填充位置。end停止填充位置，默认为数组长度
fruits.fill('orange')
fruits => ['orange','orange']
{% endhighlight %}
#### filter
检测数值元素，并返回符合条件所有元素的数组。
{% highlight js %}
// array.filter(function(currentValue,index,arr), thisValue)
numbers.filter(num => num < 3) => [1,2]
{% endhighlight %}
#### find,findIndex
返回符合传入测试（函数）条件的第一个数组元素或元素索引
{% highlight js %}
// array.find(function(currentValue, index, arr),thisValue) 返回值或者undefined
// array.findIndex(function(currentValue, index, arr), thisValue) 返回索引或者-1
{% endhighlight %}
#### forEach
数组每个元素都执行一次回调函数。
{% highlight js %}
// array.forEach(function(currentValue, index, arr), thisValue)
{% endhighlight %}
#### from
通过给定的对象中创建一个数组。
{% highlight js %}
// Array.from(object, mapFunction, thisValue)
Array.from('apple') => ['a','p','p','l','e']
Array.from(new Set(fruits)) => fruits
Array.from(numbers,num => num * 10) => [10,20,30,40,50]
{% endhighlight %}
#### includes
判断一个数组是否包含一个指定的值。
{% highlight js %}
// array.includes(searchElement,fromIndex) 查询的元素和开始的索引默认为0
fruits.includes('banana') => true
fruits.includes('pear') => false
{% endhighlight %}
#### indexOf
搜索数组中的元素，并返回它所在的位置。
{% highlight js %}
// array.indexOf(item,start) 返回索引或-1
{% endhighlight %}
#### isArray
方法用于判断一个对象是否为数组。
#### join
方法用于把数组中的所有元素转换一个字符串。元素是通过指定的分隔符进行分隔的。默认为','
{% highlight js %}
fruits.join('-') => 'apple-banana'
{% endhighlight %}
#### keys
方法用于从数组创建一个包含数组键的可迭代对象。
{% highlight js %}
const iterable = fruits.keys()
iterable.next() => {value:0,done:false}
iterable.next() => {value:1,done:false}
iterable.next() => {value:undefined,done:true}
{% endhighlight %}
#### lastIndexOf
返回一个指定的字符串值最后出现的位置，在一个字符串中的指定位置从后向前搜索。
{% highlight js %}
// array.lastIndexOf(item,start)
{% endhighlight %}
#### map
返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。
#### pop
方法用于删除数组的最后一个元素并返回删除的元素。**操作原数组**
#### push
方法可向数组的末尾添加一个或多个元素，并返回**新数组长度**，**操作原数组**
{% highlight js %}
// array.push(item1, item2, ..., itemX) 可以是多个值，如果插入的值为数组会将整个数组插入
{% endhighlight %}
#### reduce,reduceRight
将数组元素计算为一个值（从左到右）。方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。
reduceRight() 方法的功能和 reduce() 功能是一样的，不同的是 reduceRight() 从数组的末尾向前将数组中的数组项做累加。
{% highlight js %}
// array.reduce(function(total, currentValue, currentIndex, arr), initialValue)
numbers.reduce((total,num) => total+=num,10) => 10 + 1 + 2 + 3 + 4 + 5
numbers.reduceRight((total,num) => total-=num,20) => 20 - 5 - 4 - 3 - 2 - 1
{% endhighlight %}
#### reverse
反转数组的元素顺序。**操作原数组**
#### shift
删除并返回数组的第一个元素。类似pop()方法。**操作原数组**
#### slice
选取数组的的一部分，并返回一个新数组。
{% highlight js %}
// array.slice(start, end)
numbers.slice(2,4) => [3,4]
{% endhighlight %}
#### some
检测数组元素中是否有元素符合指定条件。如果有一个元素满足条件，则表达式返回true , 剩余的元素不会再执行检测。
{% highlight js %}
// array.some(function(currentValue,index,arr),thisValue)
{% endhighlight %}
#### sort
对数组的元素进行排序。排序顺序可以是字母或数字，并按升序或降序。默认排序顺序为按字母升序。当数字是按字母顺序排列时"40"将排在"5"前面。**操作原数组**
{% highlight js %}
numbers.sort((a,b) => a - b)
numbers => [1,2,3,4,5]
numbers.sort((a,b) => b - a)
numbers => [5,4,3,2,1]
{% endhighlight %}
#### splice
从数组中添加或删除元素。**操作原数组**
{% highlight js %}
// array.splice(index,howmany,item1,.....,itemX)  index索引，howmany删除多少元素可以是0，后面为添加的新元素
numbers.splice(2,2,1,2,3,4)
numbers => [1,2,1,2,3,4,5]
fruits.splice(1,0,'orange','pear')
fruits => ['apple','orange','pear','banana']
{% endhighlight %}
#### toString
把数组转换为字符串，并返回结果。
{% highlight js %}
fruits.toString() => 'apple,banana'
{% endhighlight %}
#### unshift
向数组的开头添加一个或更多元素，并返回新的长度。类似push()方法。**操作原数组**
