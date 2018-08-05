---
layout: post
title:  "javascript中的继承模式"
date:   2018-08-01 00:27:00 +0800
tags: javascript 原型 原型链 继承
---


最近在看有关原型链的问题。其中说js的继承是用原型链来完成的。具体实现是``Dog.prototype = new Animal()``，我看了很多篇文章都是这么写，但是没有说明为什么这么写，带着这个问题,我们来研究下这是为什么呢～

> ECMAScript中描述了原型链的概念，并将原型链作为实现继承的主要方法。其基本思想是利用原型让一个引用类型继承另一个引用类型的属性和方法。简单回顾一下构造函数、原型和实例的关系：每个构造函数都有一个原型对象，原型对象都包含一个指向构造函数的指针，而**实例都包含一个指向原型对象的内部指针**。那么，假如我们让原型对象等于另一个类型的实例，结果会怎么样呢？显然，此时的原型对象将包含一个指向另一个原型的指针，相应的，另一个原型中也包含着一个指向另一个构造函数的指针。假如另一个原型又是另一个类型的实例，那么上述关系依然成立，如此层层递进，就构成了实例与原型的链条。这就是所谓原型链的基本概念。

#### 类

js中没有类的语法，通过声明一个方法来实现类的概念，约定俗成类的首字母大写。一个实例有一个__proto__属性指向类的原型，类的原型prototype中有一个constructor方法为构造函数指向类本身。
{% highlight js %}
function Dog() {}
const dog = new Dog()
// dog.__proto__ === Dog.prototype
{% endhighlight %}
![]({{'/assets/img/post-2018-08-01.jpg' | absolute_url}})
#### 原型链继承方法
常用的方法就是将父类的实例赋值给子类的原型。
**原来存在于父类实例中的所有属性和方法现在也存在于子类的原型中。**
{% highlight js %}
function Animal() {
  this.type = 'animal'
  this.colors = ['red','blue','green']
}
Animal.prototype.getType = function() {
  return this.type
}

function Cat() {
  this.name = 'damao'
}
Cat.prototype = new Animal() // 将父类的实例指向子类的原型，实例内部包含指向原型的内部指针
// Cat.prototype = Animal.prototype // 无作用
Cat.prototype.constructor = Cat // 将子类的构造函数指回子类
// 一定要在实现继承后才能在原型上添加方法
Cat.prototype.getName = function() {
  return this.name
}

const miao = new Cat()
console.log(miao.getType()) // animal
console.log(miao.getName()) // damao
console.log(miao.__proto__.constructor) // [Function: Cat]
console.log(miao instanceof Cat) // true
console.log(miao instanceof Animal) // true
console.log(miao instanceof Object) // true
console.log(miao.colors) // ['r','g','b']
miao.colors.push('black')
const miao2 = new Cat()
console.log(miao2.colors) // ['r','g','b','black'] 两个实例共享一个属性
{% endhighlight %}

#### 借用构造函数
在解决原型中包含引用类型值所带来问题的过程中，开发人员开始使用一种叫做**借用构造函数**的技术（有时候也叫做伪造对象或经典继承）。这种技术的基本思想相当简单，即在子类构造函数的内部调用父类的构造函数。
{% highlight js %}
function SuperType(name) {
  this.colors = ['red','green','blue']
  this.name = name
}
function SubType(name) {
  SuperType.call(this,name)
}
let instance1 = new SubType('tom')
instance1.colors.push('black')
console.log(instance1.colors) // [ 'red', 'green', 'blue', 'black' ]
console.log(instance1.name) // 'tom'
let instance2 = new SubType('peter')
console.log(instance2.colors) // [ 'red', 'green', 'blue' ]
console.log(instance2.name) // 'peter'
{% endhighlight %}
#### 组合继承
组合继承，有时候也叫伪经典继承，指的是将原型链和借用构造函数的技术组合到一起，从而发挥二者之长的一种继承模式。即通过在原型上定义方法实现了函数复用，又能够保证每个实例都有自己的属性。
{% highlight js %}
function SuperType(name) {
  this.colors = ['red','green','blue']
  this.name = name
}
SuperType.prototype.sayName = function() {
  return this.name
}
function SubType(name,age) {
  // 继承属性
  SuperType.call(this,name)
  this.age = age
}
// 继承方法
SubType.prototype = new SuperType()
SubType.prototype.constructor = SubType
SubType.prototype.sayAge = function() {
  return this.age
}

let instance1 = new SubType('tom',15)
instance1.colors.push('black')
console.log(instance1.colors) // [ 'red', 'green', 'blue', 'black' ]
console.log(instance1.sayName()) // 'tom'
console.log(instance1.sayAge()) // 15
let instance2 = new SubType('peter',18)
console.log(instance2.colors) // [ 'red', 'green', 'blue' ]
console.log(instance2.sayName()) // 'peter'
console.log(instance2.sayAge()) // 18
{% endhighlight %}
#### 寄生组合式继承
组合继承是javascript最常用的继承模式，不过，它也有自己的不足。组合继承最大的问题是无论什么情况下，都会调用两次超类的构造函数。下面这个例子的高效率体现在它只调用了一次SuperType构造函数，并且因此避免了在SubType.prototype上面创建不必要的、多余的属性，同时原型链还能保持不变，开发人员普遍认为寄生组合式继承是**引用类型**最理想的继承模式。
{% highlight js %}
function inheritPrototype(subType,superType) {
  let prototype = Object.create(superType.prototype) // 创建对象
  prototype.constructor = SubType // 增强对象
  subType.prototype = prototype // 指定对象
}
function SuperType(name) {
  this.name = name
  this.colors = ['red','blue','green']
}
SuperType.prototype.sayName = function() {
  return this.name
}
function SubType(name,age) {
  SuperType.call(this,name)
  this.age = age
}
inheritPrototype(SubType,SuperType)
SubType.prototype.sayAge = function() {
  return this.age
}

let sub = new SubType('tom',15)
console.log(sub.sayName()) // 'tom'
console.log(sub.sayAge()) // 15

{% endhighlight %}
