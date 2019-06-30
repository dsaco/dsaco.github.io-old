---
layout: post
title:  "Typescript 开始"
date:   2018-08-12 22:49:00 +0800
tags: Typescript React react-redux react-router redux-saga webpack tslint
---

> typescript简直有毒，只要和react等框架组合在一起，坑真的源源不断的来，我真的是脑阔疼。
这次打算一步一步来，有问题记录问题，有bug解决bug。真·从头开始。

- 运行环境：mac
- 开发工具：atom （建议使用vscode）

#### 创建一个新项目dashboard，安装依赖
> 由于墙的原因先安装cnpm ``npm i -g cnpm``

{% highlight js %}
mkdir dashboard && cd dashboard
npm init -y
cnpm i -D webpack webpack-dev-server webpack-cli webpack-merge html-webpack-plugin typescript ts-loader
cnpm i -S react react-dom @types/react @types/react-dom
{% endhighlight %}
package.json的依赖如下：
{% highlight js %}
"devDependencies": {
  "html-webpack-plugin": "^3.2.0",
  "source-map-loader": "^0.2.3",
  "ts-loader": "^4.4.2",
  "tslint": "^5.11.0",
  "tslint-loader": "^3.6.0",
  "tslint-react": "^3.6.0",
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
webpack.config.js
{% highlight js %}
const path = require('path');
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const merge = require('webpack-merge');

const TARGET = process.env.npm_lifecycle_event;

const common = {
  entry: path.resolve(__dirname,'./src/index.tsx'),
  devtool: 'source-map',
  resolve: {
    extensions: ['.ts','.tsx','.js','.json'],
    alias: {
      Components: path.resolve(__dirname, './src/components/'),
    },
  },
  module: {
    rules:[
      { test: /\.tsx?$/, loader: 'ts-loader', exclude: /node_modules/ },
      { enforce: 'pre', test:/\.js$/, loader: 'source-map-loader' },
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname,'./src/index.html'),
    }),
  ],
};

if(TARGET === 'dev') {
  module.exports = merge(common, {
    mode: 'development',
    module: {
      rules: [
        { enforce: 'pre', test: /\.tsx?$/, loader: 'tslint-loader', exclude: /node_modules/ },
      ],
    },
    plugins: [
      new webpack.HotModuleReplacementPlugin(),
    ],
    devServer: {
      port: 8080,
      hot: true,
    },
  })
};

if(TARGET === 'build') {
  module.exports = merge(common, {
    mode: 'production',
    output:{
      path: path.resolve(__dirname,'dist'),
      filename: 'scripts/bundle.js',
    }
  })
};

{% endhighlight %}
tsconfig.json
{% highlight js %}
{
  "compilerOptions": {
    "sourceMap": true,
    "noImplicitAny": true,
    "noUnusedLocals": true,
    "strictNullChecks":true,
    "module": "commonjs",
    "target": "es5",
    "lib": ["DOM","ES5","ScriptHost","ES6"],
    "jsx": "react",
    "experimentalDecorators": true
  },
  "include": [
    "./src/**/*"
  ]
}
{% endhighlight %}
tslint.json
{% highlight js %}
{
  "extends":["tslint:recommended","tslint-react"],
  "rules":{
    "ordered-imports": false,
    "object-literal-sort-keys": false,
    "quotemark": [true, "single", "jsx-double"]
  }
}
{% endhighlight %}
