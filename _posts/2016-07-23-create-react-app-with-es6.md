---
layout: post
title: '用 ES6 创建一个简单的 React App'
---

React 是由 Facebook 发布的一个用于构建用户界面的 JavaScript 库。本文将介绍不借助任何生成器来使用 ES6 语法来创建一个简单的 React App。文中将会用到以下技术：

* react
* react-router
* webpack
* babel
* material-ui


## 一、目录结构

源代码主要放在 `app` 目录里，其中 `components` 中是 React 组件源代码、`images` 和 `stylesheets` 是图片和样式的相关代码，`build` 是打包生成的静态文件，`package.json` 和 `webpack.config.js` 分别是 npm 和 webpack 的配置文件：

```
app/
  components/
    App.js
    Hello.js
    Stat.js
    Vote.js
  images/
    screen-bg.jpg
  stylesheets/
    normalize.css
  index.html
  index.js
build/
.gitgnore
package.json
webpack.config.js
```


## 二、编码前的配置工作

项目中的配置文件主要有两个：npm 的配置文件 `package.json` 和 webpack 的配置文件 `webpack.config.js`。

复制下面的代码到 `package.json` 中，然后运行 `npm install` 即可完成项目所依赖的模块的安装：

~~~json
{
  "name": "vote-demo",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "webpack-dev-server --inline --content-base ./build",
    "build": "webpack"
  },
  "author": "Yanbin Ma",
  "license": "MIT",
  "dependencies": {
    "material-ui": "^0.15.2",
    "react": "^15.2.1",
    "react-dom": "^15.2.1",
    "react-router": "^2.6.0",
    "react-tap-event-plugin": "^1.0.0"
  },
  "devDependencies": {
    "babel-core": "^6.5.1",
    "babel-loader": "^6.2.2",
    "babel-preset-es2015": "^6.5.0",
    "babel-preset-react": "^6.5.0",
    "css-loader": "^0.23.1",
    "extract-text-webpack-plugin": "^1.0.1",
    "file-loader": "^0.9.0",
    "html-webpack-plugin": "^2.22.0",
    "http-server": "^0.8.5",
    "style-loader": "^0.13.1",
    "webpack": "^1.13.1",
    "webpack-dev-server": "^1.14.1"
  }
}
~~~

运行 `webpack` 命令时，会使用下面的配置将 JS、CSS、Images 等模块打包到 `build` 目录中输出：

~~~js
var ExtractTextPlugin = require("extract-text-webpack-plugin")
var HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './app/index.js',

  output: {
    path: './build',
    filename: 'bundle.js',
    publicPath: ''
  },

  module: {
    loaders: [
      { test: /\.js$/, exclude: /node_modules/, loader: 'babel-loader?presets[]=es2015&presets[]=react' },
      { test: /\.css$/, loader: "style-loader!css-loader" },
      { test: /\.(jpg|png)$/, loader: 'file-loader?name=img/[name].[hash].[ext]' }
    ]
  },

  plugins: [
    new HtmlWebpackPlugin({
      template: './app/index.html'
    }),
    new ExtractTextPlugin("styles.css")
  ]
}
~~~

关于 webpack 配置的详细语法，可以参考 [webpack 入门教程](https://hulufei.gitbooks.io/react-tutorial/content/webpack.html)。


## 三、React 和 React Router

下面我们来写第一个 React 文件。在 `webpack.config.js` 中我们定义了 App 的入口文件 `index.js`，所以现在我们首先完成它。

~~~js
import React from 'react'
import ReactDOM from 'react-dom'
import { Router, Route, hashHistory, IndexRoute } from 'react-router'
~~~


## 四、React 的组件化


## 五、React 组件库 Material UI