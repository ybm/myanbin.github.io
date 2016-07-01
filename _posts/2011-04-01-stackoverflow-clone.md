---
layout: post
title: '仿 Stack Overflow 的问答网站'
---


随着社交化问答网站 Quora 的流行，现在正在经历着一场问答网站的热潮。Stack Overflow 一个国外著名的程序员问答网站，它使用独特的投票系统、积分系统以及勋章系统，展现出一个新型的专业类问答网站。本文讲述了如何使用 PHP 和 MySQL开发一个模仿 Stack Overflow 的程序员问答网站


## 总体设计

网站采用 MVC（模型-视图-控制器）的架构方式，使用了 WAMP（Windows、Apache、MySQL 和 PHP）技术栈进行开发。

![MVC 示意图](https://infp.github.io/blogimages/qwench-mvc.png){:.center}

### 数据库设计

![数据库 Scheme 图](https://infp.github.io/blogimages/qwench-db.png){:.center}


## 编码实现

本网站主要实现了用户的注册和登录、提问与回答、搜索、投票系统和积分系统等功能。下面分别进行介绍：

### 首页

![网站首页](https://infp.github.io/blogimages/qwench-home.png){:.center}

### 用户

![网站个人用户页](https://infp.github.io/blogimages/qwench-profile.png){:.center}

### 问答

![网站问题详情页](https://infp.github.io/blogimages/qwench-question.png){:.center}

### 使用开源项目

本项目使用了以下开源项目：

* WMD：一个 JavaScript 编写的 Markdown 编辑器
* prettify：一个 JavaScript 开发的代码高亮工具


## 展望

随着社交化问答网站 Quora 的流行，现在正在经历着一场问答网站的热潮，许多各式各样的问答网站纷纷涌现。未来，预计问答网站将会朝着下面的方向发展：

* 更加专注于某一专业领域。
* 社交化与实名制。运用社交网络中的朋友链，可以将信息广泛的传播。而实名制可以聚集许多能够提供高质量内容的领域专家，提高问答网站中内容的可信度。
* 由使用者创造、编辑、整理。像维基百科一样，借助人们共同的努力，可以减少垃圾内容，积累到大量的优质内容。
* 迅速回应。一个问题被提出来的几个小时内便可被别的使用者发现，进而得到回答。这个离不开问答网站的社交化。


## 获取源代码

我把源码放到了 GitHub 上，你可以在[这里下载](https://github.com/myanbin/qwench)。