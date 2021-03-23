---
title: "ArcPy水文分析（河网分级、流域、集水区）"
author: "iPattern"
date: 2016-12-06T18:52:04+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["GIS"]
---

ArcGIS水文分析步骤较多，难以记忆，这点不得不艳羡一下QGIS那个一键水文分析。 
好在有model builder和ArcPy，最近刚好用到，写好脚本测试跑了一把，效果不错，做个记录。

其中使用的DEM数据是网上下载的aster那个，后面flowacc的自定义参数是90。

```python
# -*- coding: utf-8 -*-
# ---------------------------------------------------------------------------
# hydro.py
# Created on: 2016-12-06
# Usage: hydrology analysis
# Description: result include watershed, basin, stream(with order)
# ---------------------------------------------------------------------------

# Import arcpy module
import arcpy
arcpy.env.overwriteOutput = True
from arcpy import env
from arcpy.sa import *

# Set workspace
arcpy.env.workspace = "C:/test.gdb"

# Input DEM ratser file
DEM = "AsterDEM"

# Check SRS
sr = arcpy.Describe(DEM).spatialReference
print "Spatial Reference System:" + sr.name
# Check out any necessary licenses
print "Spatial Analyst Extension Available:"
print arcpy.CheckOutExtension("spatial")


# Process
fill = Fill(DEM)
flowdir = FlowDirection(fill, "NORMAL")
flowacc = FlowAccumulation(flowdir, "", "FLOAT")
streamrs = SetNull(flowacc, 1, "VALUE <= 90") # flowacc <=90 -> null, 90+ -> 1
streamlink = StreamLink(streamrs, flowdir)

watershedrs = Watershed(flowdir, streamlink, "VALUE")
arcpy.RasterToPolygon_conversion(watershedrs, "watershed", "NO_SIMPLIFY", "VALUE") # watershed polygon saved

streamorder = StreamOrder(streamrs, flowdir, "STRAHLER")
# Attention! this one goes wrong: stream = StreamToFeature(streamorder, flowdir, "SIMPLIFY")
StreamToFeature(streamorder, flowdir, "stream", "SIMPLIFY") # stream polyline saved

basinrs = Basin(flowdir)
arcpy.RasterToPolygon_conversion(basinrs, "basin", "NO_SIMPLIFY","VALUE") # basin polygon saved

print "All done, Check 'stream, basin, watershed' in Current Workspace."
```
————————————————
[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/53491051)
