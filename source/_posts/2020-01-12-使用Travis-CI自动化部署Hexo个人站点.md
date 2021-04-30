---
title: 使用Travis CI自动化部署Hexo个人站点
tags:
  - Travis CI
  - Hexo
mathjax: true
abbrlink: 1913110b
date: 2020-01-12 14:50:47
---

在刚开始使用Hexo+Github Pages搭建个人博客时，都是先在本地写好文章，再通过终端输入如下命令：

```bash
hexo clean
hexo g
hexo d
```

将新文章部署到Github Pages上去。初始时并未有什么不方便。

<!-- more -->

但是，以上的操作要求写文章的机器上必须需要安装hexo和Node.js环境。然而当随着使用的频繁，会发现当更换一台电脑（比如出差或者旧电脑损坏）之后，想要写博客，就需要重新安装并配置博客环境（尤其当在之前的机器上对配置做了一些内部的修改之后），经常就会发现，配置起来很繁琐，而且某些当时的配置（比如我个人对在网页上进行`latex`支持的配置，可见我的博文[在Hexo的Next主题中支持Latex](https://aipikachu.me/posts/2631/)）很难忆起做过什么修改的时候。这时就会迫切的需要能够有某种有效的方案来替代。

稍稍Google一下，发现原来这个问题早就有了，采用持续集成(**C**ontinuous **I**ntegration，简记为CI)的方法，来实现自动编译和发布代码（文本）。其中一种比较常用的方法是采用[Travis CI](https://travis-ci.org)持续集成的方案，实现个人博客的自动化部署。本文则是简单总结一下从网上学习的采用Travis CI自动化部署Hexo个人站点的流程，作为个人笔记。

***特别说明:*** 本文主要参考以下文章

* [Automatically Deploy Hexo With Travis CI](https://maologue.com/Auto-deploy-Hexo-with-Travis-CI/)
* [Hexo遇上Travis-CI：可能是最通俗易懂的自动发布博客图文教程](https://juejin.im/post/5a1fa30c6fb9a045263b5d2a)

下面开始，逐一记录关键操作流程。

### 关于Travis-CI

[**Travis CI**](https://travis-ci.org)是一个目前新兴的开源持续集成项目，通过执行预先设定的脚本完成相应的部署。

当我们每次执行`git push`命令提交修改至远程仓库时，`Travis CI`会自动检测我们的提交，然后根据配置文件`.travis.yml`帮我们自动生成、部署静态网页。




