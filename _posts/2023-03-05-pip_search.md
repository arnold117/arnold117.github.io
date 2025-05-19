---
layout: post
title: "重新启用pip search"
date:   2023-03-05
tags: [Python, pip]
comments: true
author: Arnold
toc: true
---

出于一些奇奇怪怪的原因，pip好像不能用`search`了呢。。那么有什么方法能启用类似的搜索功能呢？安装`pip_search`就可以了！

<!-- more -->

## 安装与使用

使用 `pip install pip_search` 命令进行安装

然后就可以用 `pip_search anything` 搜索了

以及，你可以使用特定的排序选项：

- `pip_search -s name`
- `pip_search -s version`
- `pip_search -s released`

如果想使用传统的 `pip search <keywords>` 搜索方式，将以下别名添加到你的 **.zshrc, .bashrc, .bash_profile** 等配置文件中

```bash
alias pip='function _pip(){
    if [ $1 = "search" ]; then
        pip_search "$2";
    else pip "$@";
    fi;
};_pip'
```

对于Fish用户，在fish shell中执行：

```bash
function pip --wraps="pip"
    set command $argv[1]
    set -e argv[1]
    switch "$command"
        case 'search'
            pip_search $argv
        case '*'
            command pip $command $argv
    end
end

funcsave pip
```

然后使用 `pip search` 进行搜索

![https://raw.githubusercontent.com/kkatayama/pip_search/master/screenshot.png](https://warehouse-camo.ingress.cmh1.psfhosted.org/2a072af67fc4695776eadd6554c0f308a27409a9/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f6b6b61746179616d612f7069705f7365617263682f6d61737465722f73637265656e73686f742e706e67)

按住 **command** 或 **ctrl** 然后点击文件夹图标，可以打开相应的超链接。

## 依赖包

- bs4
- rich
- requests



此文就到此结束啦！欢迎大家在评论区留言哦ヾ(^▽^*)))
Ciallo～(∠・ω< )⌒☆

**如果本文令你受益匪浅，愿意慷慨解囊，可以点击[这里](https://arnold117.github.io/likes/)，然后扫描二维码，一分也是爱。分享推荐给身边的朋友，不胜感激**。