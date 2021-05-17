---
title: "ArcGIS使用python进行三规合一用地调整"
author: "iPattern"
date: 2015-12-29T14:19:25+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["GIS"]
---

1.流程图

![flow](/images/posts/2015-12-28-landuse-flow.jpg)

2.在多个相关要素union叠加后的图层字段进行python分类计算。

if-elif-else一条道走到黑的python代码（未优化，感觉可重用代码比较多，等OOP拯救)

```python
SGHY( !TGCGCY! , !FKYD! , !GTYP! , !GTPC! , !TG_SKXJR! , !GXXM! , !GXXMQD! , !ZDXM! , !CG_SKXJR! , !CGYDDM!, !SKX!, !JBNT! )

def SGHY(TGCGCY,TGFK,GTYP,GTPC,TG_SKXJR,GXXM,GXXMQD,ZDXM,CG_SKXJR,CGYDDM,SKX,JBNT):
    if TGCGCY == "01":
        if TGFK == 1:
        return "三规有条件建设区"
    else:
        if GTYP == 1:
        if SKX == 1 and TG_SKXJR ==1:
            return "三规建设用地区"
        elif SKX == 1 and TG_SKXJR == 0:
            return "三规有条件建设区"
        else:
            return "三规有条件建设区"
        else:
        if GTPC == 1:
            if SKX == 1 and TG_SKXJR == 1:
                return "三规建设用地区"
            elif SKX == 1 and TG_SKXJR == 0:
                return "三规有条件建设区"
            else:
                return "三规建设用地区"
        else:
            return "三规有条件建设区"
    elif TGCGCY == "02":
        if GXXM == 1:
        if GXXMQD == 1:
        return "三规非建设用地区"
        else:
        if JBNT == 1:
            return "三规有条件建设区"
        else:
            if SKX == 1 and CG_SKXJR == 1:
            return "三规建设用地区"
            elif SKX == 1 and CG_SKXJR == 0:
            return "三规有条件建设区"
            else:
            return "三规建设用地区"
        else:
        if ZDXM == 1:
        if JBNT == 1:
            return "三规有条件建设区"
        else:
            if SKX == 1 and CG_SKXJR == 1:
            return "三规建设用地区"
            elif SKX == 1 and CG_SKXJR == 0:
                return "三规有条件建设区"
            else:
            return "三规建设用地区"
        else:
        if GTPC == 1:
            if JBNT == 1:
            return "三规有条件建设区"
            else:
            if SKX == 1 and CG_SKXJR == 1:
                return "三规建设用地区"
            elif SKX == 1 and CG_SKXJR == 0:
                return "三规有条件建设区"
            else:
                return "三规建设用地区"
        else:
            if CGYDDM in ['G1','G2']:
            return "三规非建设用地区"
            else:
            if JBNT == 1:
                return "三规有条件建设区"
                else:
                if SKX == 1 and CG_SKXJR == 1:
                return "三规建设用地区"
                elif SKX == 1 and CG_SKXJR == 0:
                return "三规有条件建设区"
                else:
                return "三规建设用地区"
    elif TGCGCY == "03":
    if SKX == 1:
        if CG_SKXJR == 1 or TG_SKXJR == 1:
            return "三规建设用地区"
        else:
            return "三规有条件建设区"
    else:
        return "三规建设用地区"
    else:
        if GTPC == 1:
            if JBNT == 1:
        return "三规有条件建设区"
        else:
         if SKX == 1 and CG_SKXJR == 1:
             return "三规建设用地区"
         elif SKX == 1 and CG_SKXJR == 0:
             return "三规有条件建设区"
         else:
             return "三规建设用地区"
        else:
            return "三规非建设用地区"
```            
————————————————
[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/50420562)