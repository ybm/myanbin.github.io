---
layout: post
title: '起名的艺术'
image: /public/img/napoleon.jpg
---



定理 1：代码应该是写给人来读的，只不过顺便能在机器执行而已。
{:.message}

代码大部分时候是用来维护的，而不是用来实现功能的，这个准则适用于大部分的软件工程。比如我所知道的一个软件系统，开发了三个月即上线使用，而用于维护的时间却是以年为单位的，开发者花大量的时间用于调整代码以确保其运行正确。

因此，编写可读代码成了用于衡量代码质量的重要标准之一（另外一个熟知的标准是正确性）。

![代码质量衡量标准](https://infp.github.io/blogimages/code-quality.jpg){:.center}


定理 2：好的代码胜过好的注释。
{:.message}

好的代码自己本身就是最好的文档。当你打算加注释的时候，问问自己“我如何才能把我的代码改善到不需增加注释？”重构自己的代码，然后使文档让其更清楚。比如下面这种毫无意义的注释，只会增加你代码文件的字节数：

```c
num += 1;           // 用户人数加 1
```

正确的做法应该是把变量起一个具有准确含义的名字：

```c
userCount += 1;
```


> There are only two hard things in Computer Science: cache invalidation and naming things.<br>
&mdash; <cite>Phil Karlton</cite>

> Never ascribe to malice, that which can be explained by incompetence.<br>
可以用无能解释的事，永远不要归咎于别人的恶意。<br>
&mdash; <cite>拿破仑一世</cite>