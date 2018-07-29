---
layout: post
title:  "Welcome to sass!~~"
date:   2018-07-26 23:29:55 +0800
tags: css api
cover: "/assets/img/home-bg.jpg"
---


一个颜色的alpha 通道可以通过 {Sass::Script::Functions#opacify opacify} 和 {Sass::Script::Functions#transparentize transparentize} 函数进行调整。 例如：

{% highlight scss %}
$translucent-red: rgba(255, 0, 0, 0.5);
p {
color: opacify($translucent-red, 0.3);
background-color: transparentize($translucent-red, 0.25);
}
{% endhighlight %}
被编译为：
{% highlight ruby %}
p {
  color: rgba(255, 0, 0, 0.9);
  background-color: rgba(255, 0, 0, 0.25); }
{% endhighlight %}
IE 滤镜需要每个颜色都包含 alpha 层， 并且得用 #AABBCCDD 这样严格的格式。你可以轻松的利用 {Sass::Script::Functions#ie_hex_str ie_hex_str} 函数对其做转换。 例如：
{% highlight scss %}
$translucent-red: rgba(255, 0, 0, 0.5);
$green: #00ff00;
div {
  filter: progid:DXImageTransform.Microsoft.gradient(enabled='false', startColorstr='#{ie-hex-str($green)}', endColorstr='#{ie-hex-str($translucent-red)}');
}
{% endhighlight %}


### @if
{% highlight scss %}
p {
  @if 1 + 1 == 2 { border: 1px solid;  }
  @if 5 < 3      { border: 2px dotted; }
  @if null       { border: 3px double; }
}

p {
  border: 1px solid; }
{% endhighlight %}
{% highlight scss %}
$type: monster;
p {
  @if $type == ocean {
    color: blue;
  } @else if $type == matador {
    color: red;
  } @else if $type == monster {
    color: green;
  } @else {
    color: black;
  }
}
p {
  color: green; }
{% endhighlight %}


### @for
{% highlight scss %}
@for $i from 1 through 3 {
  .item-#{$i} { width: 2em * $i; }
}
.item-1 {
  width: 2em; }
.item-2 {
  width: 4em; }
.item-3 {
  width: 6em; }
{% endhighlight %}

### @each
{% highlight scss %}
@each $animal in puma, sea-slug, egret, salamander {
  .#{$animal}-icon {
    background-image: url('/images/#{$animal}.png');
  }
}
.puma-icon {
  background-image: url('/images/puma.png'); }
.sea-slug-icon {
  background-image: url('/images/sea-slug.png'); }
.egret-icon {
  background-image: url('/images/egret.png'); }
.salamander-icon {
  background-image: url('/images/salamander.png'); }
{% endhighlight %}
### @while
{% highlight scss %}
$i: 6;
@while $i > 0 {
  .item-#{$i} { width: 2em * $i; }
  $i: $i - 2;
}
.item-6 {
  width: 12em; }

.item-4 {
  width: 8em; }

.item-2 {
  width: 4em; }
{% endhighlight %}
### @mixin
{% highlight scss %}
@mixin large-text {
  font: {
    family: Arial;
    size: 20px;
    weight: bold;
  }
  color: #ff0000;
}
.page-title {
  @include large-text;
  padding: 4px;
  margin-top: 10px;
}
.page-title {
  font-family: Arial;
  font-size: 20px;
  font-weight: bold;
  color: #ff0000;
  padding: 4px;
  margin-top: 10px; }
{% endhighlight %}
{% highlight scss %}
@mixin sexy-border($color, $width) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}

p { @include sexy-border(blue, 1in); }
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }
{% endhighlight %}
{% highlight scss %}
@mixin sexy-border($color, $width: 1in) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}
p { @include sexy-border(blue); }
h1 { @include sexy-border(blue, 2in); }
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }

h1 {
  border-color: blue;
  border-width: 2in;
  border-style: dashed; }
{% endhighlight %}
{% highlight scss %}
@mixin box-shadow($shadows...) {
  -moz-box-shadow: $shadows;
  -webkit-box-shadow: $shadows;
  box-shadow: $shadows;
}

.shadows {
  @include box-shadow(0px 4px 5px #666, 2px 6px 10px #999);
}

.shadows {
  -moz-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  -webkit-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
}
{% endhighlight %}
{% highlight scss %}
@mixin colors($text, $background, $border) {
  color: $text;
  background-color: $background;
  border-color: $border;
}

$values: #ff0000, #00ff00, #0000ff;
.primary {
  @include colors($values...);
}
.primary {
  color: #ff0000;
  background-color: #00ff00;
  border-color: #0000ff;
}
{% endhighlight %}
{% highlight scss %}
@mixin wrapped-stylish-mixin($args...) {
  font-weight: bold;
  @include stylish-mixin($args...);
}

.stylish {
  // The $width argument will get passed on to "stylish-mixin" as a keyword
  @include wrapped-stylish-mixin(#00ff00, $width: 100px);
}
{% endhighlight %}
{% highlight scss %}
@mixin apply-to-ie6-only {
  * html {
    @content;
  }
}
@include apply-to-ie6-only {
  #logo {
    background-image: url(/logo.gif);
  }
}
* html #logo {
  background-image: url(/logo.gif);
}
{% endhighlight %}
### function
{% highlight scss %}
$grid-width: 40px;
$gutter-width: 10px;

@function grid-width($n) {
  @return $n * $grid-width + ($n - 1) * $gutter-width;
}

#sidebar { width: grid-width(5); }
#sidebar {
  width: 240px; }
{% endhighlight %}
