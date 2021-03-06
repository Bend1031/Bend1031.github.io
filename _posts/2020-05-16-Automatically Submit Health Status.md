---
layout: post
title: 自动“提交健康状况”
date: 2020-05-16
author: Bend
header-img: img/post-bg-star.jpg
catalog: false
tags:
- quicker
- HTTP
---

因为学校要求每天都要提交两次“健康状况”，实在是繁琐，为了找一点“捷径”，顺便学习一下网络知识，锻炼一下解决问题的能力，于是有了这个想法。

## 前提条件

首先需要说明的是，在设计这个“自动化”之前，我每天需要做的，是打开一个网址，`点击`提交填报按钮，就完成了一次提交。**而且每次需要填写的信息，已经不需要再次填写，只需要点击一次提交按钮就行了。**

我用的方法呢，是用[quicker](https://www.getquicker.net/)这个软件,quicker可以讲的实在是太多了，简而言之，他就是把一套流程打包起来，变成一个动作，你只需要点击一下，就可以完成一系列操作，实在是很方便。具体想要了解的可以看看这篇文章-[Quicker -- 一种全新的Windows效率神器](https://sspai.com/post/47776)。

在这里我只是以一个动作的设计角度，来讲我是怎么做的。

## 最初版本

最初的想法是模拟人工操作，打开网页，点击，然后退出。

首先，打开quicker面板，新建一个组合动作。

![动作列表](https://cdn.bend1031.top/img/20200516192849.png)

图中就是我所有的步骤。

前两步，是我为了唤醒电脑，加的两步，目的是让电脑`苏醒过来`，不是必要的步骤。

第三步，打开你要登录的网址。由于完全打开网页的时间每次都不一样，为了尽可能地完全打开网页，我在下一步设置了一个10s的延时。

第五步：模拟鼠标的左键点击，坐标呢，就是需要点击提交的位置，这个坐标的获取我是通过 Snipaste 得到的（Snipaste截图时，会显示当前鼠标坐标）。

![](https://cdn.bend1031.top/img/20200516193113.png)

然后又是等待一段时间，输入快捷键 CTRL+W，关闭浏览器。

整个动作就结束了。

总的来说，这个动作的开发，为我确实节约一些精力，但是总是有些不讨喜的地方。例如，既然我不想提交的时候，我要傻乎乎的不能动，必须等动作执行完，才能继续使用我的电脑。还有就是实际使用中，总会遇到一些情况，导致动作卡在网页那步，需要我自己点击提交。于是，我萌生了改进这个动作的想法。

## 改进版本

上面那个动作是我二月份的时候实现的，等到了现在五月份，我已经成功搭建了一个小网站，有了一点网络知识，就有了实现这个动作的新的设想。

首先需要提前了解的是，在前面我说的那些步骤当中，最重要的一步，就是点击提交那一步。那么，这一步究竟发生了什么呢？

在，点击提交的时候，可以认为浏览器向一个网址发送了一个请求。具体可以这样理解，浏览器向学校说了这么一句话：“xxx已经提交健康状况了！”，然后学校回复：“知道啦！”。是不是很简单？这就是quicker中的一个核心网络动作-`HTTP请求`。

![改进后的动作](https://cdn.bend1031.top/img/20200516195017.png)

接下来我来一步步解释这些步骤。

第一二步，其实是为了不是每天同一时间提交，所以设置了一个三分钟的随机时间。

第三步，我们具体来看。

![HTTP请求](https://cdn.bend1031.top/img/20200516203102.png)

首先是网址，这个网址不同于我们打开网页的时候登录的网址，而是在HTTP请求的时候，浏览器发送信息的网址。这个网址是怎么来的呢？

首先，打开你要提交的网址，按下F12，然后F5刷新。可以看到右边出现了一些东西，点击Network，可以看到红框部分有一些`HTTP请求`。

![](https://cdn.bend1031.top/img/20200516203353.png)

而当我们点击提交之后，会发现多出来一个请求，这个就是你的浏览器对学校说的话！

![](https://cdn.bend1031.top/img/20200516203634.png)

我们点击它，就又会出现一些东西。

![](https://cdn.bend1031.top/img/20200516203834.png)

其中，第一行就可以看到我们要填入quicker中的网址。

然后回到quicker，第二个是`方法`，这个对应`Request Method` 可以看到其中是 POST，这个在我设置的动作里面，我失误改成了GET，但是实际上能运行，这，我现在还解释不了。

第三个是请求头，也就是你要提交的数据格式，在上面那张图上可以找到 Content-Type。

然后是 Cookie，也可以在上方黑色界面找到，它主要是证明你是谁。

最后是 User-Agent，这个不太重要，是用来说明你是用什么浏览器发送的请求。

到这里，如果HTTP请求成功了，那么整个过程就结束了。后面的步骤是我利用上期 Bark 服务，当提交成功后，向 ios 设备发送一条通知。

最后我们还需要配置这个动作定时执行。

在 quicker 的设置里，有自动运行，详见，配置文档，我设置的是每天9：30，16：30运行一次。

```
T:30 9,16 * * *:415a8298-fd47-48f5-a6f4-09
```

后面的数字就是你的动作ID。

写这篇文章还有一些缺憾。。。看日后有没有机会吧，哎！

