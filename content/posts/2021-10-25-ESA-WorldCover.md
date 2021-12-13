---
title: "欧洲航天局全球土地覆盖图"
date: 2021-10-25T12:15:55+08:00
categories: ["Programming"]
tags: ["GIS"]
draft: false
---

欧洲航天局全球土地覆盖图（`ESA WorldCover`)是在`Sentinel-1`和`Sentinel-2`数据的基础上，以`10米`的分辨率制作了`11个`不同的土地覆盖类别。

在`Sentinel-2`图像被云层长期覆盖的地区，由`Sentinel-1`数据提供补充信息。

因此，`Sentinel-1`和`Sentinel-2`数据的结合使得几乎实时更新土地覆盖图成为可能。世界地表覆盖图是为`2020年（1月1日至12月31日）`制作的，作为第五次地球观测包络计划（`EOEP-5`）的一部分，覆盖全球。

它为`生物多样性`、`粮食安全`、`碳评估`和`气候建模`等应用提供了宝贵的信息。

![Screen Shot 2021-10-25 at 1.56.37 PM](https://tva1.sinaimg.cn/large/008i3skNgy1gvrjjyl0mpj61h70u0nfu02.jpg)

对比`Esri`前不久发布的`Esri Land Cover 2020`，在使用同样的`Sentinel-2`数据源的前提下，`ESA WorldCover`质量明显更好，而且`COG` 格式在`QGIS`中渲染得更快。

![Screen Shot 2021-10-25 at 2.08.17 PM](https://tva1.sinaimg.cn/large/008i3skNgy1gvrjjs2ls3j61f70u0aqg02.jpg)

数据在线访问：

https://apps.sentinel-hub.com/eo-browser

另外`Klas Karlsson`提供了一份制作好的QGIS图层文件，可以更方便地在QGIS加载该数据。

https://raw.githubusercontent.com/klakar/geosupportsystem/master/ESA%20WorldCover%202020.qlr



更新频率：每年一次
许可证：知识共享署名4.0国际许可协议(CC BY 4.0)

你可以自由使用。

分享--以任何媒介或形式复制和重新分发材料
改编--重新混合、改造和建立在材料之上
用于任何目的，甚至商业用途。
 此许可证可用于自由文化作品。
只要你遵守许可条款，许可人就不能撤销这些自由。
根据以下条款。

署名 - 你必须给予适当的荣誉，提供许可证的链接，并说明是否进行了修改。你可以用任何合理的方式这样做，但不能以任何方式暗示许可人认可你或你的使用。
没有额外的限制--你不能应用法律条款或技术措施，在法律上限制他人做许可证允许的任何事情。