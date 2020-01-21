---
layout: post
title: 用 Notion 记录阅读与电影
date: 2020-01-21
author: Bend
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
- Notion
- 阅读
- 电影
---
临近过年，在家放假做咸鱼，同时也不忘小小折腾一下，用 Notion 做了个记录读书和电影的东西。

首先我们先来看看效果
![Notion 书架](https://raw.githubusercontent.com/Bend1031/PictureBed/master/img/20200121145534.png)
![书籍看板](https://raw.githubusercontent.com/Bend1031/PictureBed/master/img/20200121145629.png)

可以看到还是挺美观的。然后我来 ~~具体~~（简单） 说下是怎么做出来的。

## 什么是 Notion

简单来说，Notion 是一款基于网页的笔记软件，你可以在上面记录你想记录的一切，由于其功能十分强大，所以我只介绍我要用到的功能，对于其他功能，因为我还没有用到，所以也可以说暂时是无用的。

## 为什么要记录读书

1. **阅读体验混乱**：由于我在手机上有好几个阅读 APP, 所以在不同应用之间辗转之后，阅读的记录并没有在一个 APP 上，所以需要自己重新整理。

2. **为了记录生活**：阅读是生活的一部分，时间不知不觉在指尖溜走，总要用些办法留住些什么。

## 为什么要用 Notion 来记录

1. 以前也折腾过 Notion，但是总是陷入其功能繁杂的漩涡之中。后来明白了，为了用而用是没有意义的，而是当你有这个需求，而这个工具更加符合你的需求，所以你才用它。于是趁着过年，重新整理了自己的 Notion 笔记。

2. Notion 相比于其他笔记软件，更加美观，现代化（颜值即是生产力！🤣）。

3. 用表格来整理读书之类的东西是比较适合的，而 Notion 对表格的支持是比较强大的。

4. 另一方面，由于 Notion 对学生提供了无限 Page 的优惠，所以我们使用 Notion 并没有经济上的负担（只需要你拥有一个教育邮箱）。

## 具体步骤

### 表格显示

1. 首先**点击左下角**（New Page）新建一个页面（Page）, Page 在 Notion 中可以看作是最小的基本单元。

2. 选择 Database 下的 Table ，我们的书籍管理是要先形成一个数据库（即 Database），这里面有我们所有要管理的书。然后我们用 表格类型来将其显示出来，即第一张图片所显示的那样。

3. 对于每一本书，都有我们想显示的信息。例如作者、类型和阅读时间等等。我们先打开其中一项。
![](https://raw.githubusercontent.com/Bend1031/PictureBed/master/img/20200121154342.png)
新建的数据库默认只有三个属性（Name、Tags、Files），需要我们自行修改。
![](https://raw.githubusercontent.com/Bend1031/PictureBed/master/img/20200121154542.png)
点击 Add a Property 新建一个属性，名称我们可以自己修改，对于每一个属性，也有对应的类型，如文本，日期，多选等等。
![](https://raw.githubusercontent.com/Bend1031/PictureBed/master/img/20200121154907.png)

4. 全部新建完后。我的显示是这样的

![](https://raw.githubusercontent.com/Bend1031/PictureBed/master/img/20200121155116.png)
其中特别注意的是 Days 和 Onboard 两个属性，都是公式类型。公式的代码这里不给出，你可以直接将我分享的页面作为模板，直接复制到自己的页面里，直接修改每本书即可。

### 看板显示

在标题下方 Add a view 添加看板显示
![](https://raw.githubusercontent.com/Bend1031/PictureBed/master/img/20200121160146.png)

- 之后在右上角 Group by 选择 Status（即之前设置的属性），
- 设置 Filter（筛选），选择 Onboard 属性，
- Properties 可以设置自己想显示的内容。
- Sort（排序）设置为：Date -> Descending

这里是我的 [模板](https://www.notion.so/50e850400f684f9ea4ce682ab6171be7?v=866f71363d6a4edbbac104c029d69c27), 点击之后选择右上角 Duplicate 即可复制，然后粘贴到自己的页面即可。
![书籍看板](https://raw.githubusercontent.com/Bend1031/PictureBed/master/img/20200121145629.png)
