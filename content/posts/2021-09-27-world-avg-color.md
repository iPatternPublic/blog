---
title: "世界的平均色"
date: 2021-09-27T12:08:02+08:00
categories: ["Pattern"]
tags: ["Visualization","Map","GIS"]
draft: false
---

![world](/images/posts/2021-09-27-worldmap.png)

![africa](/images/posts/2021-09-27-africa.webp)

![asia](/images/posts/2021-09-27-asia.png)

![usav2](/images/posts/2021-09-27-usa_v2.webp)

![europe](/images/posts/2021-09-27-europe.webp)

![southamerica](/images/posts/2021-09-27-southamerica.webp)

### 准备工作

- 行政区域的Shapefile (.shp)
- 安装QGIS（或GDAL/Python，但安装QGIS将为你设置好一切）。
- 安装R和RStudio

### 操作流程

- 在R中写脚本，找到感兴趣的所有区域的边界BOX
- 从Sentinel-2下载这些区域的图片
- 创建了以下GDAL命令，以便对下载的图片进行地理配准，创建geotiff。
  - 根据地区的边界裁剪geotiff图片
  - 将Geotiff重新投影到一个合适的投影坐标系
  - 运行该GDAL脚本
- 将geotiff转换为pngs，并找到png的平均颜色


基本上，大部分工作在`R`中进行，包括创建`GDAL`脚本。只有运行`GDAL`脚本时短暂离开了`R`。
虽然`GDAL`脚本所做的事情可以在R中使用`qgisprocess`包来做，但`GDAL`更快。


原文：[Average colors of the world](https://erdavis.com/2021/06/26/average-colors-of-the-world/), JUNE 26, 2021 ERINRDAVIS
翻译摘录：iPattern