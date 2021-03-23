---
title: "ArcGIS对未知坐标系要素建立拓扑查错修错"
author: "iPattern"
date:  2015-06-02T09:27:05+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["GIS"]
---

ArcGIS的拓扑工具很强大，城市规划使用AutoCAD绘制的重叠、间隙等错误百出dwg文件在导入ArcGIS后就可以建立拓扑来自动查错，批量修错，非常方便。

文件地理数据库下面的要素数据集对数据的规范程度似乎要求很高，我一直没搞明白的是，即便新建同样的未知坐标系的要素数据集，要素类还是偶尔能导出进来（貌似只有第一个可以导出过来），很多时候导入报错。

最近突然想到不如直接在要素数据集里新建空白要素类，然后开始编辑，把要导入的要素类，直接复制粘贴进来（注意提前把要保留的字段在那个空白的要素类里建好）。

这样就不用在担心导入要素数据集失败了，后续建立拓扑也就水到渠成。



城规里面土地利用的面要素主要存在的拓扑错误就是overlap重叠和gap间隙，

(追加：开始前对polygon数据先来一下dissolve，这样不只是把相邻同属性数据合并，叠合的相同属性数据也合并了，自然就先减少了一部分overlap错误)

overlap错误在单一字段的要素类里使用subtract直接减去有奇效（主要应用在cad有空洞的面导入后形成多余面而未挖洞的情况以及面要素边缘未对齐的线状叠加），多字段的overlap就麻烦些，很多时候要create new feature并指定字段属性（追加：发现选中比较小的那个多边形，然后直接用Editor工具下的Clip，一步到位解决），偶尔是相同用地性质的地块就merge一下。

gap错误就更麻烦一些，要先create feature然后用编辑工具框选再merge到相邻的要素类里，dwg导入后貌似存在拟合问题，经常在道路边线处存在很多小碎gaps，很头疼。

（追加：网上看到一个补洞的批处理方法，“把面层转成线层（polygon to line），然后再转回来（feature to polygon），然后对转回来的图层执行合并（merge），最后再打散（multipart to singlepart (data management)）”，最后一步很关键）



三规合一项目在union之前切记要排除这两类很棘手的拓扑错误，不然后面统计出现各种错误就无能为力了。


[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/46324159)