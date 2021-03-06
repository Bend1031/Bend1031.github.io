---
layout:     post
title: 扫描版 PDF 文字识别并合并入原 PDF
subtitle: 双层 PDF 制作
date: 2019-07-02
author: Bend
header-img: img/post-bg-pdf.png
catalog: true
tags:
    - PDF
    - OCR
---

# 扫描版 PDF 文字识别并合并入原 PDF

最近突然想到一个需求，就是将扫描版的  PDF 转成可以被复制的格式，方便在阅读 PDF 时能够搜索。传统的，或者说在网上找的 PDF 很多都是扫描版的，类似于图片，所以并不存在复制粘贴的可能。

但现在 OCR 技术发展已经十分成熟，（Optical Character Recognition，光学字符识别，是指对文本资料的图像文件进行分析识别处理，获取文字及版面信息的过程。）所以自己觉得这样的想法实现可能还是蛮大的，所以做了一番搜索。

## 搜寻方案

通过搜索，大致确定了两条路线：

- 直接利用已有软件

- 借助编程技术实现

无疑，如果有现有软件可以直接操作的话，无疑是成本最低的方案。而借助编程实现则需要一定实践能力与编程知识。下面介绍两种方法。

## 1. 专业 PDF 软件 Adobe Acrobat Pro DC

在体验网上搜索的各种识别软件之后，得出的结论就是 Adobe Acrobat Pro DC 就是爸爸（不要问我为什么不介绍其他的软件，毕竟浪费我流量与大把时间的辣鸡软件我实在不想再花时间介绍了）。

在体验 Adobe Acrobat Pro DC 的功能后我是蛮满意的，除了少部分文字识别错误之外，其他表现很好。但是也不是没有缺点。

- 贵，o(︶︿︶)o 毕竟中国付费意识还没有很好的普及，破解无疑是一条出路，但是花费的时间成本也是值得考量的。

- 大，作为一个专业处理 PDF 的软件，在打开速度和体积控制上还是略显劣势（但是良好的效果让我还是能够忽略它的缺点，毕竟平时也不用它）。

综上，Adobe Acrobat Pro DC 是最优解，前提是你能买，或者找的到破解（不难）。

## 2. OCRmyPDF

[OCRmyPDF](https://github.com/jbarlow83/OCRmyPDF) 是我在 GitHub 上发现的完美符合我预期功能的一个工具，之所以说是工具而不是软件就是因为它并不是直接在电脑上安装就能使用（至少对广大的 Windows 用户来说是这样的）。

[OCRmyPDF 的安装使用文档](https://ocrmypdf.readthedocs.io/en/latest/index.html)

首先它的描述就和我的需求完美一致：**OCRmyPDF adds an OCR text layer to scanned PDF files, allowing them to be searched**. 

起初，在了解到它是 Python 3 的一个包时我还是蛮开心的，但是随之而来的**安装依赖**问题又深深困扰了我，OCRmyPDF 的使用需要借助其他包的辅助。所以也并不是即装即用，让人惆怅。

在经过一番尝试之后我决定暂时搁置，因为确实不是很方便。但是手上正好有一个 Linux 的树莓派，干脆就拿来用了装了下这个，为什么呢？因为在 Linux 系统下的安装只需要这么一行命令：

```
apt-get install ocrmypdf
```

当然这没有解决所有问题，但是已经解决 90%了（Windows 用户没人权啊）。OCRmyPDF 使用 Tesseract 进行 OCR ，对于中文简体用户，需要自己下语言包，但也仅仅只需要一行命令：

```
apt-get install tesseract-ocr-chi-sim
```

到此其实就可以正式的使用了，下面是使用样例

```
ocrmypdf -l chi_sim --pdf-renderer tesseract --output-type pdf source.pdf ocr.pdf
```

下面解释一下各个参数的意义

```
ocrmypdf # 我们使用的工具
-l chi_sim # 指定语言为中文简体
--pdf-renderer tesseract # PDF 渲染器使用 tesseract ，此处有些问题我还没来得及发现
--output-type pdf # 生成标准的 PDF 格式
source.pdf # 需要进行处理的文档名
ocr.pdf # 处理完生成的文档名
```

## 总结

到此就结束了，总的来说直接用软件处理是最优解，技术路线还存在一定的问题。

Bye~
