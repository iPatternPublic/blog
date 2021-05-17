---
title: "使用ArcPy进行Landsat 8 地表温度提取"
author: "iPattern"
date: 2016-10-25T18:05:31+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["GIS"]
---

最近尝试使用landsat 8 band10 和band11波段进行地表温度（Land Surface Temperature）提取，步骤挺多，开始用model builder做了个模型，可是步骤里面的参数挺多，所以整体流程还是不太清晰。想起来ArcPy，测试一把，总算跑起来了。。。也还不错。

步骤如下：

- 输入BAND10、BAND11、NDVI
- BAND 11 Gradadiance
- BAND 11 遥感温度
- BAND 10 Gradadiance
- BAND 10 遥感温度
- 植被覆盖率（NDVI换算）
- 计算LSE
- BAND 10 地表温度
- 保存最终的平均地表温度栅格

## 代码

编写另存.py文件，然后从命令行用python 2运行（前面输出坐标系统神马的是跑来测试玩的）：
```python
# -*- coding: utf-8 -*-
# ---------------------------------------------------------------------------
# LST.py
# Created on: 2016-10-20 By dx
# Description: Calculate Land Surface Temperature with Landsat 8 Data
# Reference: https://www.youtube.com/watch?v=uDQo2a5e7dM , Usman Buhari
# ---------------------------------------------------------------------------

# Import arcpy module
import arcpy
arcpy.env.overwriteOutput = True
from arcpy.sa import *
# Set workspace
arcpy.env.workspace = "E:/GIS/Input/test.gdb"
print "Input Data Finish: (BAND10,BAND11,NDVI)"
print arcpy.Exists("BAND10"),arcpy.Exists("BAND11"),arcpy.Exists("NDVI")
sr = arcpy.Describe("BAND10").spatialReference
print "Spatial Reference System:"
print sr.name

# Check out any necessary licenses
print "Spatial Analyst Extension Available:"
print arcpy.CheckOutExtension("spatial")


# Local variables:
# Input 
BAND10 = Raster("BAND10")
BAND11 = Raster("BAND11")
NDVI = Raster("NDVI")

# BAND 11 Gradadiance
BAND11Gradiance = BAND11 * 0.0003342 + 0.1

# BAND 11 Satelite Temperature
BAND11SatTemp = 1201.14 / Ln(480.89 / BAND11Gradiance + 1)  - 272.15

# BAND 10 Gradadiance
BAND10Gradiance = BAND10 * 0.0003342

# BAND 10 Satelite Temperature
BAND10SatTemp = 1321.08 / Ln(774.89 / BAND10Gradiance + 1)  - 272.15

# Proportion of Vegetation from NDVI, according to Carlson & Ripley, 1997
PropVEG = Square((NDVI + 1)/(1 -(-1))) # a missing bracket in this line, cause an error on the next line...

# Deriving LSE (0.004 * PropVEG+0.986)
LSE = 0.004 * PropVEG + 0.986

# BAND 10 Land Surface Temperature
BAND10LST = BAND10SatTemp / 1 + BAND10 * (BAND10SatTemp / 14380) * Ln(LSE)
BAND11LST = BAND11SatTemp / 1 + BAND11 * (BAND11SatTemp / 14380) * Ln(LSE)
# Save Final Land Surface Temperature Raster
LST = (BAND10LST+BAND11LST)/2
LST.save("LST")
print "All done, Please Check the 'BAND10LST' Raster in Current Workspace."
```

运行时LSE那一行报错了，还是’Syntax Error: invalid syntax’这么no apparent reason的错误，实在找不到为什么，只看到vs code把LSE和下两行的变量蓝色显示了，随手一搜万能的google居然在stackoverflow给了个类似的答案，原因是上一行最后少加了一个括号。。。醉了 
[http://stackoverflow.com/questions/24237111/syntax-error-invalid-syntax-for-no-apparent-reason]

挖坑

改版后CSDN这markdown好强，很多没试过的功能，表格什么的，下次更新顺便试一下，把一些参数来源具体解释一下，比如272.15这个存疑。

参考资料：一个YouTube视频和一篇ArcGIS Blog文章。
1.https://www.youtube.com/watch?v=uDQo2a5e7dM
2.https://blogs.esri.com/esri/arcgis/2014/01/06/deriving-temperature-from-landsat-8-thermal-bands-tirs/

————————————————
[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/52925629)
