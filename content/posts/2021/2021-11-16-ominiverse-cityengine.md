---
title: "利用Omniverse和ArcGIS CityEngine进行协作式城市规划"
date: 2021-11-16T12:15:55+08:00
categories: ["Design"]
tags: ["Omniverse","CityEngine"]
draft: false
---


2021-11-09
Taisha Fabricius

> "`Omniverse` "（直译：全能宇宙）这个词听起来就已经很刺激了，不是吗？

几年前（2018年）参观游戏开发者大会（GDC）时，我也被邀请参加NVIDIA `Omniverse`实时3D协作和模拟平台的演示。它被设置在一个酒店房间里（我当时感到很奇怪，甚至给同事留了言，如果两小时内没有回去，就去酒店找我：）。

很快，我就明白了，**`Omniverse`不仅仅是一个很酷的名字，它还是一个非常有前途的概念，有可能改变创作者、工程师和设计师一起工作的方式。**在那个酒店房间里，我盯着一个巨大的LED电视屏幕，看着一个人在`虚幻引擎 UE`中改变泰迪熊皮毛的粗细，而另一个人同时在`Autodesk 3ds Max`中为一把椅子建模。他们使用这些不同的软件来调整和改变东西，却在我面前的同一个场景中，实时地改变。

我对此印象深刻，想知道`ArcGIS CityEngine`在这个世界里是否也有一席之地。这些3D工作流程在许多行业中都是非常重要的。

随着`Omniverse`的发展，`CityEngine`团队一直关注着它。当英伟达开始向`Autodesk Revit`和`Rhino3D`等其他应用程序发布`Omniverse`连接器时，我们也加入了这一行列，并创建了一个内部原型和一个演示视频，在去年春天的英伟达`GTC`上获得了一些关注。

该演示还促成了**Jack Dangermond**（Esri公司首席执行官）和**Bob Pette**（英伟达公司专业可视化副总裁）在同一会议上关于地理空间计算的对话。

半年之后，`GTC`又来了，时间是11月8日至11日，我们终于可以发布**Omniverse Connector for CityEngine 2021.1**。

![NVIDIA GTC Fall 2021 Collaborative Urban Planning in Omniverse with ArcGIS CityEngine](https://tva1.sinaimg.cn/large/008i3skNgy1gwhbgiwxi5j31kw0sgdnf.jpg)

你现在就可以测试了! 确保已经安装了CityEngine 2021.1，然后前往NVIDIA `Omniverse`，下载启动器，你将在 "Exchange "部分看到CityEngine的连接器。

![Omniverse Connector for CityEngine](https://tva1.sinaimg.cn/large/008i3skNgy1gwhbnhhk6cj30p40pm77z.jpg)

用于CityEngine的`Omniverse`连接器
这是该连接器的第一次迭代。鉴于`Omniverse`庞大而复杂的生态系统，我们仍在探索可能的用户体验。我们这个版本的主要用例是采用Revit BIM模型，并为其提供一个城市背景。

我们开始在现有的USD导出器上建立`Omniverse`连接器，并将其扩展为能够方便地将模型发送到`Omniverse`服务器。

![CityEngine Omniverse Connector](https://tva1.sinaimg.cn/large/008i3skNgy1gwhbnrten6j30b00cg3z7.jpg)

正如你所看到的，只有几个简单的必要选项。设定保存位置和文件名称即可。

仅仅因为一个建筑需要改动而重新导出大型城市模型很不优雅，恰恰`USD`格式和`Omniverse`有一个解决方案，可以进入实时同步和`USD`分层技术。

`USD`允许我们简单地隐藏不符合需求的建筑，并在上面分层增加一个更新版本。这正是我们添加到`Omniverse`连接器的方法。如果连接器检测到`Omniverse`服务器上有相同名称（如`/Users/CityEngine/myCity/myCity_root.usdc`）的先前输出（如`myCity`），它将非破坏性地将新模型分层在现有数据之上并隐藏过时的模型。