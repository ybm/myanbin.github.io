---
layout: post
title: '用 ES6 创建一个简单的 React App'
---

React 是由 Facebook 发布的一个用于构建用户界面的 JavaScript 库。本文将介绍使用 ES6 语法来创建一个简单的 React App。文中将会用到以下技术：

* react
* react-router
* webpack
* babel
* material-ui


## 一、目录结构

下面是一种简单的目录结构形式。源代码主要放在 `app` 目录里，其中 `components` 是 React 组件源代码文件、`index.js` 是 App 的入口文件、`images` 和 `stylesheets` 则保存项目中用到的图片和样式：

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

首先运行 `npm install` 命令完成 `package.json` 中所列出的模块的安装。

然后，按照下面的代码配置 webpack：

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

配置完成之后，我们来写第一个 React 文件。

在 `webpack.config.js` 中我们定义了 App 的入口文件 `index.js`，所以现在我们首先完成它。

开始，我们首先应该载入 `react` 和 `react-router` 两个模块：

~~~js
import React from 'react'
import ReactDOM from 'react-dom'
import { Router, Route, hashHistory, IndexRoute } from 'react-router'
~~~

> 在 ES6 中，可以使用 `import` 语句加载 JavaScript 模块，使用 `as` 关键字可以对模块进行重命名

然后使用 React Router 进行路由的配置。下面的代码指出了 Router 应该如何匹配 URL 并且调用相应的组件：

~~~js
class App extends React.Component {
  render() {
    return (
      <div>
        {this.props.children}
      </div>
    )
  }
}

ReactDOM.render((
  <Router history={hashHistory}>
    <Route path="/" component={App}>
      <IndexRoute component={Hello} />
      <Route path="/vote" component={Vote} />
      <Route path="/stat" component={Stat} />
    </Route>
  </Router>
), document.getElementById('app'))
~~~

当用户访问 `/` 时，便会使用默认路由 IndexRoute 定位到组件 `Hello`；访问 `/vote` 时，便会指向到 `Vote` 组件。

最后，React 会将这个配置好的 Router 绑定到 ID 为 `app` 的 DOM 上。


## 四、React 的组件化

从上面的目录结构中可以看到，我们将 React 的组件写在与它同名的 JavaScript 中。在这个文件中，我们不仅会定义这个组件的 DOM 结构和交互行为，还会将 CSS 样式写在其中，这样当我们需要使用这个组件时，直接调用组件即可，其相应的 JS 和 CSS 便会同时被加载。

下面是 `Hello` 组件的源码：

~~~js
import React from 'react'
import background from '../images/screen-bg.jpg'

import io from 'socket.io-client'

const styles = {
  screen: {
    backgroundImage: `url(${background})`,
    backgroundSize: 'cover',
    height: 'calc(100vh - 64px)'
  }
}

class Hello extends React.Component {

  componentDidMount() {
    console.log('wellcome to hello screen');
  }

  render() {
    return (
      <div style={styles.screen}></div>
    )
  }
}

export default Hello
~~~

以上代码中使用了 ES6 的模板字符串（template strings）语法：在被 <code>`</code> 括起来的字符串内部，可以直接插入 JavaScript 变量。


## 五、React 组件库 Material UI

[Material UI](https://github.com/callemall/material-ui) 是一个明星级的开源 React 组件库，使用 ES6 语法实现了 Google 的 Material Design 设计规范。

下面的代码中，导入并使用了 Material UI 的标题栏组件 AppBar：

~~~js
import React from 'react'
import injectTapEventPlugin from 'react-tap-event-plugin'
import MuiThemeProvider from 'material-ui/styles/MuiThemeProvider'
import AppBar from 'material-ui/AppBar'

injectTapEventPlugin()

class App extends React.Component {
  render() {
    return (
      <MuiThemeProvider>
        <div>
          <AppBar title="Vote Demo App" />
          {this.props.children}
        </div>
      </MuiThemeProvider>
    )
  }
}
~~~




## 获取源代码

我把源码放到了 GitHub 上，你可以在[这里下载](https://github.com/xinhuaorg/vote-demo)。