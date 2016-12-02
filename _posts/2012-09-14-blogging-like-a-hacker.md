---
layout: post
title: "像黑客一样写博客"
---


一直以来我在寻求一种写博客的最佳体验，我厌倦了复杂的博客系统，只需要一个容易维护的博客程序，而能够专注于写作。就在一个月前，我了解到 [Jekyll](https://jekyllrb.com)，于是打算重新设计我的博客。而今天，这个博客终于问世了。


Jekyll 是用 Ruby 开发的一个静态站点生成器，它会根据网页源码生成静态文件。它提供了模板、变量、插件等功能，所以实际上可以用来编写整个网站。只需要使用下面的几行命令，就可以在本地生成一个博客：


~~~sh
$ gem install jekyll
$ jekyll new myblog
$ cd myblog
$ jekyll server
# => Now browse to http://localhost:4000
~~~

最后，利用 GitHub Page，将博客源代码部署到 GitHub 上去，便可以得到一个使用版本控制，可以在本地用 [Markdown](http://wowubuntu.com/markdown/basic.html) 写作的简单快速的静态博客系统了。
