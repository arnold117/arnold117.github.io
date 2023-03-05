---
layout: post
title: "大数据的各类资料(停止更新。)"
date:   2022-03-06
tags: [BigData]
comments: true
author: Arnold
toc: true
---

学习云计算与大数据的各类资料！停止更新

<!-- more -->

老师叫我们安装这个列表里的软件，，，
![](./../images/2022/03/06/big_data_navigate/soft_list.png)

我看到这个云盘内容我人都是懵的：这是什么，那是什么，怎么样安装，怎么样的安装顺序？？完全搞不懂啊喂！

## 1. Linux操作系统
列表提供的是UbuntuKylin-16.04，是国产的换皮系统，资源占用太多，踢出更新列表！

**END OF LIFE**

**But！我会更新标准的Ubuntu的安装使用等资源！  
请查看博客带有标签Linux的文章！**

## 2. 其中的Windows软件
先把里面几个.exe的拎出来，让我看看你的真面目！

### 1. putty
官网([点我访问！](https://www.putty.org/))

PuTTY是一款集成虚拟终端、系统控制台和网络文件传输为一体的自由及开放源代码的程序。它支持多种网络协议，包括SCP，SSH，Telnet，rlogin和原始的套接字连接。它也可以连接到串行端口。

em，对我来说好像没什么用，我习惯拿Windows Terminal了，暂时搁置吧。
### 2. FileZilla
官网([点我访问！](https://filezilla-project.org/))  
中文网([点我访问！](https://www.filezilla.cn/))

FileZilla是一种快速、可信赖的FTP客户端以及服务器端开放源代码程序，具有多种特色、直觉的接口。

em，好像暂时也用不到，因为我喜欢使用SCP命令传输，，搁置一下！  
**有关于SCP命令的博客！**
### 3. VirtualBox
官网([点我访问！](https://www.virtualbox.org/))

Oracle VirtualBox是由德国InnoTek软件公司出品的虚拟机软件，现在则由甲骨文公司进行开发，是甲骨文公司xVM虚拟化平台技术的一部分。它提供用户在32位或64位的Windows、Solaris及Linux 操作系统上虚拟其它x86的操作系统。

但是我使用VMware和Hyper-V啊，踢出更新列表！

**END OF LIFE**

### 4. SecurAble
因为Liunx下rar压缩包不常见，就检查了一下。

官网([点我访问！](https://www.grc.com/securable.htm))

这软件，怎么说呢，特别过时。新的计算机不用考虑这个软件检测的功能，都是标配，不会减配。踢出更新列表！

**END OF LIFE**

## 3. Linux 软件
剩余应该都是

### 1. Eclipse
[官网](https://www.eclipse.org/)

Eclipse是一款跨平台开源集成开发环境。最初主要用来Java语言开发，目前亦有人通过插件使其作为C++、Python、PHP等其他语言的开发工具。 Eclipse的本身只是一个框架平台，但是众多插件的支持，使得Eclipse拥有较佳的灵活性，所以许多软件开发商以Eclipse为框架开发自己的IDE。

我使用没有图形界面的 Ubuntu Server，对我来说没有什么用，踢出更新列表！

**END OF LIFE**

### 2. Oracle JDK
[官网](https://www.oracle.com/java/technologies/downloads/)

em, 不用介绍了吧。

目前JDK主要两个，Oracle JDK和OpenJDK，功能上没有什么差别。  
Hadoop依赖于JDK8，而Oracle JDK8的安装过于复杂，于是我选择 openJDK, Ubuntu下安装只需要一行命令：
```
sudo apt install openjdk-8-jdk
```

### 3. Maven

### 4. MySQL Java connector

### 5. Mongo Java Driver

### 6. SBT

### 7. Hadoop
[官网](https://hadoop.apache.org/)

Apache Hadoop是一款支持数据密集型分布式应用程序并以Apache 2.0许可协议发布的开源软件框架。

### 8. HBase

### 9. Hive

### 10. Spark

### 11. Flink

### 12. Spark Streaming Kafka

### 13. Kafka

### 14. Redis