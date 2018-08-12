---
layout: post
title:  "Typescript 第一节"
date:   2018-08-12 22:49:00 +0800
tags: typescript react react-redux react-router redux-saga webpack tslint
---

> typescript简直有毒，只要和react等框架组合在一起，坑真的源源不断的来，我真的是脑阔疼。
这次打算一步一步来，有问题记录问题，有bug解决bug。真·从头开始。

- 运行环境：mac
- 开发工具：atom （建议使用vscode）

#### 创建一个新项目dashboard，安装依赖
> 由于墙的原因先安装cnpm ``npm i -g cnpm``

{% highlight ruby %}
mkdir dashboard && cd dashboard
npm init -y
cnpm i -D webpack webpack-dev-server webpack-cli webpack-merge html-webpack-plugin typescript ts-loader
cnpm i -S react react-dom @types/react @types/react-dom
{% endhighlight %}
package.json的依赖如下：
{% highlight ruby %}
"devDependencies": {
  "html-webpack-plugin": "^3.2.0",
  "ts-loader": "^4.4.2",
  "typescript": "^3.0.1",
  "webpack": "^4.16.5",
  "webpack-cli": "^3.1.0",
  "webpack-dev-server": "^3.1.5",
  "webpack-merge": "^4.1.4"
},
"dependencies": {
  "@types/react": "^16.4.9",
  "@types/react-dom": "^16.0.7",
  "react": "^16.4.2",
  "react-dom": "^16.4.2"
}
{% endhighlight %}
---
#### 配置文件















------
