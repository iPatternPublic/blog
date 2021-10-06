---
title: "美国四季的色彩"
date: 2021-10-06T21:42:49+08:00
categories: ["Pattern"]
tags: ["Visualization","Map","GIS"]
draft: false
---


**Data Stuff**的上一篇文章《世界的平均颜色》，只描绘了世界在夏天的样子，其他季节的颜色会有很大的不同。

要活的世界的季节性平均颜色需要合适的数据集，而处理原始的Landsat或Sentinel数据则过于耗时繁琐。

幸运的是，EOX的Petr Sevcik提供并帮助作者使用了`SInergise`数据集。120米分辨率，10天间隔的全球无云图像，非常符合要求。

不幸的是，这些文件是巨大的，按通道（红/绿/蓝/等波段）分割，并存储在AWS云的S3中。作者花了不少时间研究如何下载这些文件并将它们重新组合起来。如果你想自己做的话，文末的原文链接里有源代码提供。

好了，这就是那张Data Stuff花几十个小时制作的一张你只会看几秒钟的地图：

![gif](/images/posts/2021-10-06-usa-color.webp)


GIF很好地显示了雪的消退和绿色植物的发展。

9月的白带是去年在美国西海岸的那场可怕野火的烟雾。




原文：https://erdavis.com/2021/09/07/average-seasonal-colors-of-the-usa/

翻译摘录：iPattern