---
title: "ArcGIS使用ArcScan完成道路边线生成道路中线"
author: "iPattern"
date: 2015-03-11T11:41:31+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["GIS"]
---

手上有一套城市规划主干道道路边线的dwg文件，想拿他生成道路中线，试了几种办法未果，看到有网友推荐使用ArcScan去做，就尝试了一下，效果还不错，精度够规划层面使用。

记录一下操作过程如下：

1. 由于手上的dwg有很多缺陷，主要问题是很多地方未连接上，所以先对道路边线polyline建立拓扑，规则不能有悬挂点。

然后修复拓扑错误，用拓扑修复工具，框选，右键snap->trim->select feature&delete（大概是这种顺序操作流程，snap不能解决就trim然后delete，有的还得去extend）。

2. Feature to polygon，将修复好的polyline转面。

3. Polygon to Raster，像元大小设为5m。

4. Reclassify，道路栅格非空值设为1，Nodata设为0.

5. 新建一个要素类，类型为polyline，这个是给转换后的道路中线用的。

6. 确认扩展里勾选ArcScan，然后打开ArcScan工具条，在重分类之后的道路栅格上右键-开始编辑，此时ArcScan工具条处于激活状态。

7. 在Vectorization里设置下Vectorization Settings（最大宽度什么的，按道路宽和栅格大小设置下就好，还有预定义的等高线、平行线什么的设置可选）

8. 点一下Show Preview就可以预览生成情况了，不满意就回去改设置再来。（这个有点像Adobe illustrator的那个Image Trace）

9. Generate Features就可以把生成的道路中线保存到第5步建立的polyline要素类里。

10. Editor-save edits-stop editing。大功告成！


[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/44196685)