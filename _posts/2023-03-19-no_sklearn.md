---
layout: post
title: "No module named sklearn报错的解决方案"
date:   2023-03-19
tags: [Python, sklearn]
comments: true
author: Arnold
toc: true
---

明明用了pip安装sklearn，为什么报错呢？

<!-- more -->
你是不是使用了
``` bash
pip install sklearn
```
来安装sklearn的呢？如果是的话，那么你就会遇到这个问题。

查看版本，发现sklearn的版本0.0.post1。这是为什么呢？

查看官网，发现sklearn的安装包名是`scikit-learn`，而不是`sklearn`。所以，正确的安装方法是：
``` bash
pip install scikit-learn
```
安装完成后，再次`import sklearn`，问题解决。

此文就到此结束啦！欢迎大家在评论区留言哦ヾ(^▽^*)))
Ciallo～(∠・ω< )⌒☆

**如果本文令你受益匪浅，愿意慷慨解囊，可以点击[这里](https://arnold117.github.io/likes/)，然后扫描二维码，一分也是爱。分享推荐给身边的朋友，不胜感激**。