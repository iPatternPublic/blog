---
title: "用开源/免费软件做设计"
author: "iPattern"
date: 2019-04-15T00:00:00+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["Creative","Open-source"]
---

## 拥抱开源

前阵子，首张黑洞图片的事爆出来一堆黑心商家以版权相要挟，漫天开价要求巨额赔偿的事。更可恶的是它们根本就没有这张图片的版权，还被网友扒出来把国旗国徽的图片挂网售卖，甚至形成了“维权-诉讼-和解-签约”的钓鱼维权模式。



版权之争，触目惊心，可见一斑。



作为一个不那么正经的设计师，各类大牌设计软件自然是买不起的（可能也有瞧不上的...），那么是时候总结一下怎样用开源或免费软件做设计了。



有句话叫“国外一开源，国内就自主创新了”，这个，哈哈，不多说，希望本次分享能促进达成 “软件一开源，设计师就省钱”的小目标。当然，也希望小伙伴们赚钱后饮水思源去捐赠支持开源项目。



以下开始分享大厂商业软件们的免费/开源替代品


## Adobe

Adobe全家桶一直是众多设计师居家旅行必备良药，但是它搞的这个付费订阅销售策略有点伤不起，一次性买断都够贵了，现在给了钱还只能“租用”。。。



要不是这样，估计一次买断，价格不贵的Affinity也不会这么快崛起，并迅速铺开产品线，以Photo/Designer/Publisher分别对标PS/AI/ID。



不过撇开他们两家，我们有开源免费的选择：

- Photoshop

> GIMP / KRITA

- Illustrator

> INKSCAPE

- Indesign

> Scribus



## Autodesk

一直不喜欢Autodesk家的软件，个个身宽体胖，真当每个设计师家里有超算啊！！还有AutoCAD每年一个版本，越来越大，真正常用到的功能却不见改善和新增，见过很多设计师一直停留在AutoCAD2008甚至2004，不知道是不是这个原因。



至于3ds Max和Maya，（同AutoCAD）几乎不用不想说话，我爱Blender，它建模、渲染、剪视频啥都能做。再至于有点跑题的Rhinoceros & Grasshopper么，Blender有参数化插件Sverchok又或者Python脚本可以一战。



### AutoCAD

> BRL-CAD / FreeCAD /LibreCAD

### 3ds Max | Maya

> Blender

多说一句，Blender 简直是开源软件之光，甚至在“很多”方面超越了“很多”商业软件。


### ArcGIS

Esri出品的ArcGIS，尤其是新版的ArcGIS Pro，不消说，除了贵（以及不支持MacOS）啥都好 😭 。而且不是一般的贵，是贵可贵，非常贵！！虽然个人非商业版一年授权的价格还不错，但是请高度注意它的授权使用范围。

不过话说回来，最近几年各类WebGIS（在线Mapping）网站崛起，OSM，Mapbox，Google Earth之类的选择也非常多，甚至国内的高德、百度地图的开放平台做的也不错，实在是用户之幸。

虽然在线搞事情很方便，少不了还是有很多数据需要本地处理的，QGIS这时候就是不二之选了，基本上常用的ArcGIS功能都有（水文分析甚至一个命令全套做完，比ArcGIS还便利）。

> QGIS


### Microsoft Office

近期似乎用到office的场景越来越少了，虽然融入了微软Fluent Design的office365越来越漂亮。


写文本有很多优秀轻便的Markdown软件，比如Typora，Bear之类的；

做PPT，额...似乎很久没做了，而且回想起大乱炖，一锅粥式的PPT有点怵，还是乔帮主（Steve Jobs）的Keynote做的“重剑无锋，大巧不工”啊；

至于Excel，确实是神器，用数据验证和VBA能玩出很多花来。


不过我们还是有以下竞品可以替代：LibreOffice几乎就是个开源的MS Office了，Google Docs作为Web APP非常方便，WPS对MS Office兼容性比较好（非开源，个人版免费，广告呵呵哒）。

> LibreOffice

### Lumion

对于渲染类的软件，似乎趋势在于实时、交互，（相对静态的V-Ray很强，但是Blender自带的Cycles 也很强），这方面目前游戏引擎走在前沿。比如巨头虚幻引擎（Unreal）正在免费公测的Unreal Studio 有种宫中大王巡游到穷乡僻壤（规划设计行业）教训小弟（Lumion）的感觉

> Unreal Studio


## Windows | MacOS

说着说着就到了操作系统，Bug 10 （Windows 10）系统自2015年7月正式推出以来，这几年真是把用户当作小白鼠来折腾，各种强制更新，更新后bug不断，撤回更新的事情“屡错屡犯”。Image直到2018年的秋季更新1809版才似乎稳定下来。



至于高雅的MacOS，一般情况下安心享用就好了。毕竟不少人在PC上折腾过“黑苹果”（Hackintosh），不过想要完美的体验，最终还是要老老实实入坑“白苹果”，然后轻抚Touchpad/Magic Trackpad，神清气爽叹一句：“真香！”。


Anyway， 面对Bug10隔三岔五的滋扰，厨子（Tim Cook）虎视眈眈你的钱包，我们还有第三个选择：Linux。
不过Linux桌面有点像安卓一样（安卓底层也是Linux），面临严重的碎片化问题，版本众多，但是换个角度看，用户们有很多优秀的选择也不错。

以下就三个我使用过的Linux系统及个人看法：

> Fedora / Manjaro / Ubuntu

Redhat 系的Fedora界面沉静，体验连贯，是巨头Redhat（刚被IBM收购）的社区版本，各类特性走在前沿。

Arch 系的Manjaro安装简单，界面清秀，滚动更新，浩瀚的AUR几乎能无痛安装各种最新软件，适合稍爱折腾的人~

Debian 系的Ubuntu用户量巨大，稳如老狗，是很多人转向Linux的第一站。