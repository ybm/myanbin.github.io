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

下面是一种简单的目录结构形式。源代码主要放在 `app` 目录里，其中 `components` 是 React 组件源代码文件、`images` 和 `stylesheets` 是图片和样式的相关代码，`index.js` 是入口文件：

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

除了手动生成文件目录外，还可以通过 Facebook 官方的 [Create React App](https://github.com/facebookincubator/create-react-app) 来自动生成。


## 二、编码前的配置工作

项目中的配置文件主要有两个：npm 的配置文件 `package.json` 和 webpack 的配置文件 `webpack.config.js`。

首先运行 `npm install` 命令完成 `package.json` 中所列出的模块的安装。然后按照下面的代码配置 webpack：

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
      {
        test: /\.js$/,
        exclude: /node_modules/,
        loader: 'babel-loader?presets[]=es2015&presets[]=react'
      },
      {
        test: /\.css$/,
        loader: "style-loader!css-loader"
      },
      {
        test: /\.(jpg|png)$/,
        loader: 'file-loader?name=img/[name].[hash].[ext]'
      }
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

开始，我们首先应该载入 `react` 和 `react-router` 两个模块：

~~~js
import React from 'react'
import ReactDOM from 'react-dom'
import { Router, Route, hashHistory, IndexRoute } from 'react-router'
~~~

> 在 ES6 中，可以使用 `import` 语句加载 JavaScript 模块

## 四、React 的组件化

（待完成）


## 五、React 组件库 Material UI

[Material UI] 是一个明星级的 React 组件库，使用 ES6 语法实现了 Google 的 Material Design 设计规范。
