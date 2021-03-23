---
title: "萨凡纳城市设计参数及CityEngine实现"
author: "iPattern"
date: 2019-04-13T00:00:00+08:00
description: "This is meta description"
categories: ["Programming"]
tags: ["Urban Design"]
---

## 01 原始参数来源
![](/images/posts/2019-04-savannah-1-book.webp)

在维基百科Oglethorpe_Plan词条和乔治亚州百科的Savannah City Plan词条下（请参考本公众号前两篇翻译文章）对各项尺度皆有所描述，但均不完整，而且和Google Map上测量出的街坊尺度有较大出入。意外的是《The Grove Encyclopedia of American Art》一书(p381)详细记载萨瓦纳城市设计原始参数，包括街坊（Ward）和两级四类道路的详细尺寸。暂且忽略实际规划实施中所作的调整，下面以原始参数进行解释。

![](/images/posts/2019-04-savannah-02-pr.webp)

![](/images/posts/2019-04-savannah-03-pr.webp)

## 02 原始参数详解

STEP 1: 南北向三等分，东西向四等分
![](/images/posts/2019-04-savannah-04-s1.webp)


STEP 2: 中心留出广场 Square
![](/images/posts/2019-04-savannah-05-s2.webp)

STEP 3: 围绕广场，南北设置4个Tything，东西设置2个Trust
![](/images/posts/2019-04-savannah-06-s3.webp)

STEP 4: 街道与细分
![](/images/posts/2019-04-savannah-07-s4.webp)

两个等级 四种类型的街道
![](/images/posts/2019-04-savannah-08.webp)



## 03 CityEngine简介

什么是CityEngine？
![](/images/posts/2019-04-savannah-09.webp)




> CityEngine是先进的3D建模软件，可以在比传统建模技术更短的时间内创建巨量、交互、沉浸式的城市环境。 使用CityEngine创建的城市可以基于真实的GIS数据，也可用于展示过去，现在或未来的虚拟城市。



> CityEngine的CGA形状语法是一种用于生成建筑3D内容的独特编程语言。 术语CGA代表Computer Generated Architecture（计算生成建筑）。 基于语法建模的思路是通过定义CGA规则来创建越来越多的细节以迭代改进设计。 这些规则对一定范围（scope）内的几何体形状进行操作。 下图展示了这一过程：最左侧为初始形状，最右侧是生成的模型。

![](/images/posts/2019-04-savannah-10.jpeg)



## 04 CityEngine实现



好了，Esri“重"器CityEngine的官方介绍完毕，接下来。。。

“ 
Talk is cheap.

 
Show me the code.

 ”
-- Torvalds, Linus (2000-08-25)



除去凑数的，不到80行，码完

![](/images/posts/2019-04-savannah-11.webp)

放大看看细节，Tything的20' 30' 60'三种"茴香豆"的写法，啊，细分....随机出现有木有？！

![](/images/posts/2019-04-savannah-12.jpeg)

和Google Map小飞机扫的倾斜摄影模型对比一下

![](/images/posts/2019-04-savannah-13.webp)

前方放大，埋个彩蛋~~

![](/images/posts/2019-04-savannah-14.webp)




算了，憋不住了，这个彩蛋就是阿甘正传片头长凳所在的齐佩瓦广场（Chippewa Square），没错！就是在这里拍的，不过现在据说长椅已经不在了。。

![](/images/posts/2019-04-savannah-15.webp)



关键部分CGA rule
```
Ward -->
  split(z){
      ~1: WardPartSN
      |CIVIC_STREET_SECONDARY_WIDTH: CivicStreetSecondary
      |~1:WardPartM
      |CIVIC_STREET_SECONDARY_WIDTH: CivicStreetSecondary
      |~1:WardPartSN}

WardPartSN -->
  split(x){~1:TythingBlock
      |CIVIC_STREET_PRINCIPAL_WIDTH: CivicStreetPrincipal
      |~1:TythingBlock}    
TythingBlock -->
  split(z){~1:Tything|UTILITARIAN_STREET_LANE_WIDTH:UtilitarianStreetLane|~1:Tything}


WardPartM -->
  split(x){~1: TrustBlock
      |CIVIC_STREET_SECONDARY_WIDTH: CivicStreetSecondary
      |~2:Square
      |CIVIC_STREET_SECONDARY_WIDTH: CivicStreetSecondary
      |~1:TrustBlock}
TrustBlock -->
  split(z){~1:Trust
      |CIVIC_STREET_PRINCIPAL_WIDTH:CivicStreetPrincipal
      |~1:Trust}
```