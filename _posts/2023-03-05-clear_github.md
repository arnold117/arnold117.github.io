---
layout: post
title: "清除Github上Commit记录"
date:   2023-03-05
tags: [Git]
comments: true
author: Arnold
toc: true
---

把项目提交到 GitHub 上，有时候可能不小心提交了一些隐私信息，如密码和邮箱。如何删除这些记录，形成一个全新的仓库，并且保持代码不变呢？

<!-- more -->

* 新建一个空分支

  ``` bash
  git checkout --orphan latest_branch
  ```

* 添加所有的文件

  ```bash
  git add -A
  ```

  注意，此时可能会产生新文件，可以先行删除。

* 提交空信息

  ```bash
  git commit -am "."
  ```

* 强制删除旧分支

  ```bash
  git branch -D master
  ```

  如果旧分支名称不是 `master`，可以自行更改

* 当前分支改为旧分支名称

  ```bash
  git branch -m master
  ```

* 强制推送到远程仓库

  ```bash
  git push -f origin master
  ```

  此时检查一下Github，就会发现所有的commit信息都被清理了呢。
  
  

此文就到此结束啦！欢迎大家在评论区留言哦ヾ(^▽^*)))
Ciallo～(∠・ω< )⌒☆

**如果本文令你受益匪浅，愿意慷慨解囊，可以点击[这里](https://arnold117.github.io/likes/)，然后扫描二维码，一分也是爱。分享推荐给身边的朋友，不胜感激**。