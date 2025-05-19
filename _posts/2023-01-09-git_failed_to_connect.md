---
layout: post
title: "Git使用SSH报错：Failed to connect to github.com port 22 (或443) 的解决方案"
date:   2023-01-09
tags: [Git]
comments: true
author: Arnold
toc: true
---

这类错误常见于使用了科学上网工具的童鞋。常见的错误代码有如下：
```
fatal: unable to access '{repository}': Failed to connect to github.com port 22: Connection refused

fatal: unable to access '{repository}': Failed to connect to github.com port 443 after 21092 ms: Timed out
```
本文将针对不同的错误代码给出解决方案。
<!-- more -->

## 1. Failed to connect to github.com port 22: Connection refused
该错误通常是因为使用TAP设备，如Clash TAP Device和Clash TUN Mode，默认22端口被TAP设备占用而导致SSH无法正常工作。解决方案如下：

找到`~/.ssh/config`文件，没有的话新建一个。  
该文件在Windows操作系统的路径一般为`C:\Users\{Username}\.ssh\config`  
在`Host github.com`内追加如下内容，没有则创建条目：
```
Host github.com
  Hostname ssh.github.com
  Port 443
```
即可将端口设置为不和TAP设备冲突的443端口。

## 2. Failed to connect to github.com port 443: Timed out
该错误通常是因为使用本地代理，但git中没有配置代理而导致SSH无法正常工作。解决方案如下：

找到`~/.ssh/config`文件，没有的话新建一个。  
该文件在Windows操作系统的路径一般为`C:\Users\{Username}\.ssh\config`  
在`Host github.com`内追加如下内容，没有则创建条目：

在MacOS和Linux下：
```
Host github.com
    Hostname ssh.github.com
    Port 443
    ProxyCommand nc -v -x 127.0.0.1:1086 %h %p
```
其中1086为代理端口，如果不是1086请自行修改。

是在Windows下：
```
Host github.com
    Hostname ssh.github.com
    Port 443
    ProxyCommand connect -S 127.0.0.1:1086 %h %p
```
这里`-S`表示使用`socks5`代理, 如果是`http`代理则为`-H`。connect工具git自带, 在\mingw64\bin\下面.

此文就到此结束啦！欢迎大家在评论区留言哦ヾ(^▽^*)))  
Ciallo～(∠・ω< )⌒☆​  
写文不易，如果你觉得我的文章对你有帮助，欢迎[打赏](https://arnold117.github.io/likes/)！