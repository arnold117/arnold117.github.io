---
layout: post
title: "Ubuntu Server 18.04安装Hadoop 3.1.3"
date:   2022-03-07
tags: [BigData]
comments: true
author: Arnold
toc: true
---

使用Ubuntu Server 18.04安装Hadoop 3.1.3。  
虚拟机快照真是个好东西，有快照真的随便造！

<!-- more -->

## 1. 安装JDK
Hadoop 3.1.3要求JDK8及以上，由于OpenJDK与OracleJDK无显著特异性差异，我选择安装OpenJDK:
```
apt install openjdk-8-jdk
```

## 2. 创建hadoop用户
```
useradd -r -m -s /bin/bash hadoop
passwd hadoop
adduser hadoop sudo
```
并切换到Hadoop用户
```
su hadoop
```

**待续！**

以后也用不到了，封存。