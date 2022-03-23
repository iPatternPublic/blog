---
title: "iPattern周刊 2"
date: 2021-05-17T01:39:00+08:00
categories: ["weekly post"]
tags: ["Mapbox","Blender"]
draft: false
---

## 1

> Blender 配合插件Scatter 4.0制作的细节惊人的植物群落。

@Martin Klekner

![Image](https://tva1.sinaimg.cn/large/008i3skNgy1gqkrzteeojj30u015v7wh.jpg)

![Image](https://tva1.sinaimg.cn/large/008i3skNgy1gqkrzyw41tj30u015v7m0.jpg)


## 2
> 来自@der_flow_的年度提醒，不要使用PNG格式的图片做动画。

虽然很多人告诉你它是做网页或什么的很好的格式，但不要把它们用于图像序列。如果你想知道为什么你的电脑（比如在After Effects中工作）很慢，那很可能是你在使用PNG。

读/写（或去/压缩）PNG比使用TIF/EXR文件时要慢10倍。请帮你自己和你的编译器一个忙，停止使用PNG。如果你担心文件大小，请使用带有LZW压缩的TIF文件。

至于网页，比较好的图片格式是webp。

![Image](https://tva1.sinaimg.cn/large/008i3skNgy1gqks03xtvuj31e709b0uk.jpg)

## 3

> Mapbox最近推出了一项新功能，允许你在Mapbox Studio内使用不同类型的可视化方式直接对外部数据进行可视化。

- 等值域地图
- 数据驱动的圆
- 数据驱动的线
- 三维挤出图

这篇博文介绍了完全在Mapbox Studio内使用数据驱动圆圈创建伦敦市中心Airbnb地点的以下可视化的步骤。每个圆圈代表一个房源，所有的房源都根据其价格段进行着色。



https://datavis.blog/2021/05/14/mapbox-data-visualisation-component/



![img](https://tva1.sinaimg.cn/large/008i3skNgy1gqks0dvlf0j30yy0m7npd.jpg)



## 4

> 不知道在任何现代规划或建筑法规中，这将打破多少个规范和原则？比如通道、坡度、停车、保护等等，但人们还是喜欢它。🤔

@createstreets

圣弥额尔山（法语：Mont-Saint-Michel，天主教中文称“圣弥额尔山”）是法国诺曼底附近，距海岸约1公里的岩石小岛，为法国旅游胜地，也是天主教徒的朝圣地，山顶建有著名的圣弥额尔山隐修院。圣弥额尔山及其海湾于1979年被联合国教科文组织列为世界遗产。

![Mont-Saint-Michel](https://tva1.sinaimg.cn/large/008i3skNgy1gqksd8u56nj30u00w9do5.jpg)

## 5

Pyodide

> Pyodide可以用于任何你想在网络浏览器中运行Python的情况。

Pyodide通过WebAssembly将Python 3.8的运行时间和Python科学堆栈（包括NumPy、Pandas、Matplotlib、SciPy和scikit-learn）一起带到浏览器中。软件包目录中列出了超过75个目前可用的软件包。此外，还可以从PyPi安装纯Python wheels。

Pyodide提供了Javascript和Python之间对象的透明转换。当在浏览器中使用时，Python可以完全访问Web APIs。

![Pyodide](https://tva1.sinaimg.cn/large/008i3skNgy1gqksd2djeej30b4052q32.jpg)

