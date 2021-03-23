---
title: "ArcGIS使用python进行三规合一用地调整"
author: "iPattern"
date: 2015-12-29T14:19:25+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["GIS"]
---

对图斑（polygon，File Geodatabase）进行自上而下，从左往右次序编号。

1.添加两个字段：`xmin`和`ymax`，数据类型均为浮点数。

2.对`xmin`字段使用`python`代码 `!shape.extent.XMin!` 计算出`xmin`数值。


![index](/images/posts/2015-08-12-arcgis-index-1.png)




3.对`ymax`字段使用`python`代码 `!shape.extent.YMax!` 计算出`ymax`数值。

4.使用工具箱内的`Sort` （Data Management）首先输入`ymax`字段，倒序排列；然后输入`xmin`字段，顺序排列。即可计算出按次序排列的新`OBJECTID`。


![index](/images/posts/2015-08-12-arcgis-index-2.png)




5.标注`OBJECTID`或者新建字段（计算数据等于`OBJECTID`）来标注。

————————————————
[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/47445159)
