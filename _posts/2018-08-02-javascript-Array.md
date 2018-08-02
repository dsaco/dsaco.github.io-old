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
从数组的指定位置拷贝元素到数组的另一个指定位置中。操作原数组
{% highlight js %}
//array.copyWithin(target,start,end)
numbers.copyWithin(2,1,3)
//numbers => [1,2,2,3,5]
{% endhighlight %}




//es6
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.entries();
entries() 方法返回一个数组的迭代对象，该对象包含数组的键值对 (key/value)。
迭代对象中数组的索引值作为 key， 数组元素作为 value。


every() 方法用于检测数组所有元素是否都符合指定条件（通过函数提供）。
every() 方法使用指定函数检测数组中的所有元素：
如果数组中检测到有一个元素不满足，则整个表达式返回 false ，且剩余的元素不会再进行检测。
如果所有元素都满足条件，则返回 true。

//es6 ,原数组操作
array.fill(value, start, end)
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.fill("Runoob");


filter() 不会改变原始数组。
array.filter(function(currentValue,index,arr), thisValue)
filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

//es6
array.find(function(currentValue, index, arr),thisValue)
find() 方法返回通过测试（函数内判断）的数组的第一个元素的值。
find() 方法为数组中的每个元素都调用一次函数执行：
当数组中的元素在测试条件时返回 true 时, find() 返回符合条件的元素，之后的值不会再调用执行函数。
如果没有符合条件的元素返回 undefined

findIndex() 方法返回传入一个测试条件（函数）符合条件的数组第一个元素位置。
findIndex() 方法为数组中的每个元素都调用一次函数执行：
当数组中的元素在测试条件时返回 true 时, findIndex() 返回符合条件的元素的索引位置，之后的值不会再调用执行函数。
如果没有符合条件的元素返回 -1

array.forEach(function(currentValue, index, arr), thisValue)


Array.from(object, mapFunction, thisValue)
var myArr = Array.from("RUNOOB");
var arr = Array.from([1, 2, 3], x => x * 10);
// arr[0] == 10;
// arr[1] == 20;
// arr[2] == 30;

//es6
arr.includes(searchElement, fromIndex)
let site = ['runoob', 'google', 'taobao'];
site.includes('runoob');
// true
site.includes('baidu');
// false

array.indexOf(item,start)
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple"); //2

isArray() 方法用于判断一个对象是否为数组。

var fruits = ["Banana", "Orange", "Apple", "Mango"];
var energy = fruits.join();
join() 方法用于把数组中的所有元素转换一个字符串。
元素是通过指定的分隔符进行分隔的。

//es6
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.keys();
keys() 方法用于从数组创建一个包含数组键的可迭代对象。
如果对象是数组返回 true，否则返回 false。


var fruits = ["Banana", "Orange", "Apple", "Mango"];
var a = fruits.lastIndexOf("Apple");
lastIndexOf() 方法可返回一个指定的字符串值最后出现的位置，在一个字符串中的指定位置从后向前搜索。
array.lastIndexOf(item,start)

array.map(function(currentValue,index,arr), thisValue)
返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。

//操作原数组
pop() 方法用于删除数组的最后一个元素并返回删除的元素。
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.pop();

//操作原数组
push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度。
array.push(item1, item2, ..., itemX)
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.push("Kiwi")


reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。
reduce() 可以作为一个高阶函数，用于函数的 compose。
array.reduce(function(total, currentValue, currentIndex, arr), initialValue)
var numbers = [15.5, 2.3, 1.1, 4.7];
function getSum(total, num) {
    return total + Math.round(num);
}
function myFunction(item) {
    document.getElementById("demo").innerHTML = numbers.reduce(getSum, 0);
}

reduceRight() 方法的功能和 reduce() 功能是一样的，不同的是 reduceRight() 从数组的末尾向前将数组中的数组项做累加。

//颠倒数组中元素的顺序： 操作原数组
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.reverse();


//操作原数组
//shift() 方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift()


array.slice(start, end)
var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
var citrus = fruits.slice(1,3);
slice() 方法可从已有的数组中返回选定的元素。
slice()方法可提取字符串的某个部分，并以新的字符串返回被提取的部分。
slice() 方法不会改变原始数组。

var ages = [3, 10, 18, 20];
function checkAdult(age) {
    return age >= 18;
}
function myFunction() {
    document.getElementById("demo").innerHTML = ages.some(checkAdult);
}
some() 方法用于检测数组中的元素是否满足指定条件（函数提供）。
some() 方法会依次执行数组的每个元素：
如果有一个元素满足条件，则表达式返回true , 剩余的元素不会再执行检测。
如果没有满足条件的元素，则返回false。


//操作原数组
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();
sort() 方法用于对数组的元素进行排序。
排序顺序可以是字母或数字，并按升序或降序。
默认排序顺序为按字母升序
var points = [40,100,1,5,25,10];
points.sort(function(a,b){return a-b});

var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();
fruits.reverse();
Orange,Mango,Banana,Apple

//操作原数组
splice() 方法用于插入、删除或替换数组的元素
array.splice(index,howmany,item1,.....,itemX)
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2,0,"Lemon","Kiwi");

toString() 方法可把数组转换为字符串，并返回结果。
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.toString();
Banana,Orange,Apple,Mango

//操作原数组
array.unshift(item1,item2, ..., itemX)
unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。
