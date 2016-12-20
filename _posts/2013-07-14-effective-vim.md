---
layout: post
title: "高效使用 Vim 编辑器"
---

<style>
  .post table th:first-child {
    width: 100px;
  }
</style>


Vim 是程序员最广泛使用的文本编辑器之一（在 Unix 文化里，它的对手是 [Emacs](https://zh.wikipedia.org/wiki/Emacs)，并由此引发了黑客界的[编辑器之战](https://zh.wikipedia.org/wiki/编辑器之战)）。

本文将会介绍一些实用的配置和命令，以便高效地使用 Vim 进行编辑。这些技巧均不需要安装任何额外的插件。

## 一、使用相对行号

在 Vim 中，相对行号是提高移动效率的一大利器。通过它可以快速定位目标位置距当前光标的行数，然后使用类似 `7j` 或 `11k` 的命令进行移动操作。

![使用相对行号后的 Vim](https://infp.github.io/blogimages/vimrc.png){:.center}

下面的配置会使 Vim 对当前行显示绝对行号，而对其它行显示相对行号：

```vim
set number
set relativenumber
```

## 二、更多的快捷键，更高的效率

“不要使用方向键，使用 `h/j/k/l` 替代！”，这句话通常是给 Vim 新手的第一条建议。Vim 中内置了丰富的快捷键，几乎所有能想到的功能，都可以通过组合快捷键来实现。所以，了解越多的快捷键和命令，就意味着更高的效率。


下面是网上一个流传广泛的 Vim 快捷键键位图（右键可以查看大图）：

![Vim 快捷键](https://infp.github.io/blogimages/vim-classic.gif){:.center}

然而这只是 Vim 快捷键的冰山一角。

