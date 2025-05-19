---
layout: post
title: "在Python 和 Jupyter 中使用 MATLAB"
date:   2022-04-02
tags: [MATLAB, Python, Jupyter]
comments: true
author: Arnold
toc: true
---

在 MATLAB 里虽然有 **Live Script** 功能，但其只能在MATLAB里编辑，且渲染和导出都比较慢，尤其导出中文时会有格式错误，不便于阅读。  
之前有段时间在 `Jupyter` 上写过Python代码，觉得挺方便的；也了解过在`Python`中调用`MATLAB`，所以就想在`Jupyter`中使用MATLAB，来看看怎么弄吧。

<!-- more -->

## 0. 准备工作
我假设你已经在**Windows电脑上**安装好了如下软件：
1. MATLAB 2020b  
2. Anaconda (Python 3.8)  

如果你和我一样不喜欢环境被污染，则打开 Anaconda 新建一个环境。  
我新建了一个叫做matlab-python的环境。

## 1. 安装用于 Python 的 MATLAB 引擎 API
打开MATLAB的安装目录，并进入如下路径：
`${matlabroot}\extern\engines\python`
在该路径打开CMD，输入命令
```
python setup.py install
```

## 2. 安装 matlab-kernel
打开CMD，如果你和我一样先创建了一个环境，则先进入环境。  
执行命令：
```
pip install matlab_kernal
python -m matlab_kernel install
```

## 3. 检查是否安装成功
输入以下命令：
```
jupyter kernelspec list
```
如果能看到MATLAB，则说明已经正确安装。接下来，就可以在 Jupyter 里使用 MATLAB了！

此文就到此结束啦！欢迎大家在评论区留言哦ヾ(^▽^*)))  
Ciallo～(∠・ω< )⌒☆​  
写文不易，如果你觉得我的文章对你有帮助，欢迎[打赏](https://arnold117.github.io/likes/)！