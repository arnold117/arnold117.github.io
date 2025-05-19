---
layout: post
title: "增强Windows系统安全性的小妙招"
date:   2023-10-26
tags: [Windows, Security Enhancement, UAC]
comments: true
author: Arnold
toc: true
---

前几天参加了1024程序员节，听了一场关于Windows系统安全性的分享，收获颇丰，于是决定将分享内容整理一下，分享给大家。

<!-- more -->

## 1. 为什么要增强Windows系统安全性
Windows系统是目前使用最广泛的操作系统，也是黑客攻击的主要目标。Windows系统的安全性一直是人们关注的焦点，而Windows系统的安全性又与用户的安全意识息息相关。

大部分用户在使用Windows系统时，为了方便，会按照网页上、或者已安装软件的提示将系统的安全性设置的很低，这样会给黑客攻击提供了便利。

因此，我们需要提高用户安全意识，增强Windows系统的安全性，从而保护我们的隐私和财产安全。

## 2. 设置按下Ctrl+Alt+Delete解锁屏幕
设置按下`Ctrl+Alt+Delete`解锁屏幕，可以防止恶意软件伪造登录界面，从而窃取用户密码。同时，开启此功能后，系统只接受实体键盘的输入，防止虚拟键盘的输入，避免了远程解锁的风险。

可以通过以下步骤开启此功能：
1. 按下`Win+R`，输入`netplwiz`，打开用户账户界面
2. 进入`高级`选项卡，勾选`要求用户按Ctrl+Alt+Delete`，点击`确定`保存设置
3. 重启系统，按下`Ctrl+Alt+Delete`，查看是否弹出登录界面

我们也可以通过修改注册表的方式来开启此功能：
1. 按下`Win+R`，输入`regedit`，打开注册表编辑器
2. 进入`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon`，找到`DisableCAD`，将其值改为`0`，保存设置
3. 如果没有`DisableCAD`，则新建一个`DWORD`类型的键，命名为`DisableCAD`，将其值改为`0`，保存设置

如果想要关闭此功能，将`DisableCAD`的值改为`1`即可。

通过以上步骤，我们就可以开启按下`Ctrl+Alt+Delete`解锁屏幕的功能了。

## 3. 将UAC设置为最高级别
UAC(User Account Control)是Windows系统中的用户账户控制功能，可以防止恶意软件通过提权的方式获取管理员权限，从而对系统进行破坏。

默认情况下，UAC的级别为第二级别，即在应用在更改计算机时，会弹出提示框，询问用户是否允许此操作。一些恶意软件可以通过模拟用户点击的方式，绕过UAC的提示框，从而获取管理员权限。

而将UAC设置为最高级别后，不论是应用程序还是用户，都需要在提示框被选定同意后才能进行操作，这样可以防止恶意软件通过提权的方式获取管理员权限。

我们可以通过以下步骤将UAC设置为最高级别：
1. 进入`控制面板`，点击`用户账户`，点击`更改用户账户控制设置`
2. 将滑块移动到最高级别，点击`确定`保存设置

这样，我们就将UAC设置为最高级别了。

## 4. 设置使用管理员权限时需要输入密码
默认情况下，用户在使用管理员权限时，不需要输入密码，这样会给恶意软件提供了便利，因此我们需要设置使用管理员权限时需要输入密码。

我们可以通过以下步骤设置使用管理员权限时需要输入密码：
1. 按下`Win+R`，输入`regedit`，打开组策略编辑器
2. 进入`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`，找到`ConsentPromptBehaviorAdmin`，将其值改为`3`，保存设置

如果想要关闭此功能，将`ConsentPromptBehaviorAdmin`的值改为`5`即可。

## 5. 及时安装安全补丁
Windows系统的安全补丁可以修复系统中的漏洞，防止恶意软件利用漏洞攻击系统。因此，我们需要及时安装安全补丁。

我们可以通过以下步骤安装安全补丁：
1. 按下`Win+R`，输入`ms-settings:windowsupdate`，打开Windows更新界面
2. 点击`立即更新`，等待更新完成
3. 重启系统，查看是否安装成功

如果安装失败，可以通过以下步骤手动安装安全补丁：
 1. 按下`Win+R`，输入`ms-settings:windowsupdate`，打开Windows更新界面
 2. 点击`查看更新历史记录`，查看更新失败的补丁
 3. 访问[微软官网](https://www.microsoft.com/zh-cn/download/windows.aspx)，下载对应的安全补丁
 4. 双击安全补丁，按照提示安装即可


此文就到此结束啦！欢迎大家在评论区留言哦ヾ(^▽^*)))
Ciallo～(∠・ω< )⌒☆

**如果本文令你受益匪浅，愿意慷慨解囊，可以点击[这里](https://arnold117.github.io/likes/)，然后扫描二维码，一分也是爱。分享推荐给身边的朋友，不胜感激**。