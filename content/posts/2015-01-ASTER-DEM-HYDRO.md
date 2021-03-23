---
title: "ArcGIS使用ASTER GDEM V2 全球数字高程数据进行水文分析"
author: "iPattern"
date: 2015-01-30T17:43:33+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["GIS"]
---

所需DEM数据可从地理空间数据云下载，对操作过程和经验阈值做个记录。

## 1.Fill

z值默认，即填充所有洼地。得到FillDEM，下一步使用。

## 2.Flow Direction

得到Flowdir

## 3.Flow Accumulation

得FlowAcc，下一步使用。

## 4.Raster Calculator

提取河网。公式及经验值为： SetNull("FlowAcc"<=90,1)

## 5.Stream to Feature

转为矢量河网

## 6.Stream Link

## 7.Watershed 集水区

这一步的出水口点要素要事先做好，默认的好像是河网交叉口（前阵子在youtube上看到一个水文分析，出水口是手工在河网交叉口点的，对，是手工点的）

或者在第二项输入streamlink数据亦可。



备注：大范围的Basin单独算即可，只需要FlowDir数据。


[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/43309281)
