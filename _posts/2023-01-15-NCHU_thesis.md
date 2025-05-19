---
layout: post
title: "南昌航空大学本科生毕业设计相关文件LaTex模板"
date:   2023-01-15
tags: [LaTex, Thesis, NCHU]
comments: true
author: Arnold
toc: true
---

此文是对南昌航空大学本科生毕业设计相关文件LaTex模板相关介绍、使用方法和链接。

<!-- more -->

## 介绍

众所周知，Word文档的痛苦程度是随着页数的增加而指数上升的，在使用过程中很容易出现格式错误，而且难以排查。而LaTex的优势在于，文档的格式是由代码控制的，因此在编写过程中可以很方便地检查格式错误，而且可以很方便地修改格式。此外，LaTex的文档可以很方便地转换为PDF格式，因此可以很方便地打印。

为了方便南昌航空大学本科生毕业设计相关文件的编写，减少重复劳动，提高效率，我编写了四个LaTex模板。

该套模板包括任务书、开题报告、毕业论文（含原创性声明）、进度登记表四个部分。

各文档预览：
![](../images/2023/01/15/mission.png)
![](../images/2023/01/15/Pr.png)
![](../images/2023/01/15/thesis.png)
![](../images/2023/01/15/records.png)

模板均使用LaTex编写，使用方法见下文。

## 使用方法
有两种方式进行编辑和编译：

* Overleaf 在线编译
* 本地编译

> 推荐使用 Overleaf 在线编译的方式。

### Overleaf 在线编译
**强烈建议大家使用**  

Overleaf 是一个十分方便的网页版在线 LaTeX 编辑器。如果是 Overleaf 会员用户的话，甚至可以与 Github 同步。

![](https://i.loli.net/2021/01/31/OMbfg7Pza3xdGlR.png)

1. 在项目界面，选择 Download ZIP
2. 在 Overleaf 页面的 New Project，Upload Project，上传第 1 步下载的 zip 文件
3. 点击左上角的 Menu 按钮，设置 Compiler 类型为 XeLaTeX，然后点击 Recompiler，即可查看编译好的页面

### 本地编译

本地编译需要安装 TeX 发行版软件，例如 TeX Live、MacTeX 和 MikTeX，这些发行版都自带了基本的 LaTeX 编译工具。

**注意**：系统需要安装有宋体（SimSun），楷体（SimKai）和黑体（SimHei）字体以及 Times New Roman 英文字体，**并请不要使用 CTeX**。

#### Windows

可以在系统中安装 TeX Live 或者 MikTeX。

#### Mac

可以在系统中安装 MacTeX 或者 MikTeX 或者是 TeXShop。

#### Linux

可以在系统中安装 TeX Live 或者 MikTeX。

#### 配置 VSCode + LaTeX Workshop

1. 在 VSCode 左侧的插件栏搜索 LaTeX Workshop 并安装

2. 下载或者克隆本模版，用 VSCode 打开项目文件夹

3. 点击打开`main.tex`文件，点击左下角的`√`的符号，选择第一项`Build LaTex Project`

4. 选择`Recipe: latexmk (xelatex)`

    即在 Tex Live 环境下，使用xekatexmk进行编译

5. 如果是使用 MikTeX，中途会提示安装宏包。等左下角再次显示`√`，再点击，选择第二项`View LaTeX PDF`，即可进行预览。

## 各模板链接
任务书: [arnold117/NCHU_Bachelor_Mission_Statement_Template](https://github.com/arnold117/NCHU_Bachelor_Mission_Statement_Template)

开题报告: [arnold117/NCHU_Bachelor_Proposal_Report_Template](https://github.com/arnold117/NCHU_Bachelor_Proposal_Report_Template)

毕业论文（含原创性声明）: [arnold117/NCHU_Bachelor_Thesis_Template](https://github.com/arnold117/NCHU_Bachelor_Thesis_Template)

进度登记表: [arnold117/NCHU_Bachelor_Work_Records_Template](https://github.com/arnold117/NCHU_Bachelor_Work_Records_Template)

## 引用说明
上述模板均可免费使用，在使用时请在论文参考文献中引用：
### 任务书
``` bibtex
@article{zhou7538093,
  author = {Zhou, Yanuo},
  title = {NCHU Bachelor Mission Statement Template},
  year = {2023},
  publisher = {Zenodo},
  doi = {10.5281/zenodo.7538093},
  month={Jan}
}
```
Zhou, Yanuo. (2023). NCHU Bachelor Mission Statement Template. Zenodo. https://doi.org/10.5281/zenodo.7538093

### 开题报告
``` bibtex
@article{zhou7538095,
  author = {Zhou, Yanuo},
  title = {NCHU Bachelor Proposal Report Template},
  year = {2023},
  publisher = {Zenodo},
  doi = {10.5281/zenodo.7538095},
  month={Jan} 
}
```
Zhou, Yanuo. (2023). NCHU Bachelor Proposal Report Template. Zenodo. https://doi.org/10.5281/zenodo.7538095

### 毕业论文
``` bibtex
@article{zhou7538087,
  author = {Zhou, Yanuo},
  title = {NCHU Bachelor Thesis Template},
  year = {2023},
  publisher = {Zenodo},
  doi = {10.5281/zenodo.7538087},
  month={Jan} 
}
```
Zhou, Yanuo. (2023). NCHU Bachelor Thesis Template. Zenodo. https://doi.org/10.5281/zenodo.7538087

### 进度登记表
``` bibtex
@article{zhou7538089,
  author = {Zhou, Yanuo},
  title = {NCHU Bachelor Work Records Template},
  year = {2023},
  publisher = {Zenodo},
  doi = {10.5281/zenodo.7538089},
  month={Jan}
}
```
Zhou, Yanuo. (2023). NCHU Bachelor Work Records Template. Zenodo. https://doi.org/10.5281/zenodo.7538089

并请在致谢中注明模板作者：[arnold117](https://arnold117.github.io/)。

此文就到此结束啦！欢迎大家在评论区留言哦ヾ(^▽^*)))  
Ciallo～(∠・ω< )⌒☆​  
写文不易，如果你觉得我的文章对你有帮助，欢迎[打赏](https://arnold117.github.io/likes/)！