---
title: "禅意 300元树莓派4做设计开发电脑"
date: 2021-05-04T22:53:00+08:00
categories: ["experiment"]
tags: ["Raspberry Pi"]
draft: false
---

<iframe src="//player.bilibili.com/player.html?aid=757522336&bvid=BV1t64y1S7qo&cid=323469733&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> 
</iframe>

<figure class="video_container">
  <iframe src="https://www.youtube.com/embed/enMumwvLAug" frameborder="0" allowfullscreen="true"> </iframe>
</figure>


300元的树莓派4可以做日常开发设计电脑吗？

可。 

节能环保，静音禅意。

即刻获得乔帮主一直追求的不打扰人思考的Fanless，再也没有台式机和笔记本风扇恼人的噪声，以及电表催人奋进的紧迫感了。



闲时功耗2.7w，满载不过6.4w，与动辄几百瓦的台式主机相比，四舍五入约等于无。

| Pi 4 State                       | Power Consumption |
| :------------------------------- | :---------------- |
| Idle                             | 540 mA (2.7 W)    |
| `ab -n 100 -c 10` (uncached)     | 1010 mA (5.1 W)   |
| 400% CPU load (`stress --cpu 4`) | 1280 mA (6.4 W)   |

数据来源：www.pidramble.com

## 开源软件和ARM架构的积极影响越发突出

### 高可用性的开源软件

> 开源软件（英语：open source software，缩写：OSS）又称开放源代码软件，是一种源代码可以任意获取的计算机软件，这种软件的版权持有人在软件协议的规定之下保留一部分权利并允许用户学习、修改以及以任何目的向任何人分发该软件。 - Wikipedia 

在设计领域，开源软件最突出的优势可能就是`高可用性`，无需面对商业软件高昂的售价、复杂的授权，只需一台电脑，不管是Windows、MacOS、Linux甚至BSD操作系统，均可以直接获取到你需要的软件工具。

### 低功耗高性能的ARM架构

自苹果公司2020年宣布用两年时间将Mac电脑从`Intel` x86架构芯片过渡到自行设计的`ARM`架构芯片，并推出`M1`芯片的一系列Mac新品以来，`ARM`架构开始跳出移动领域，在生产力电脑领域展现出不可思议的低功耗、高性能优势。

同为ARM架构的树莓派4虽然性能不能与M1相提并论，但是在轻量应用上已经具备相当出色的性能，双4K画面输出能力也可以实现高生产力的双屏办公。

树莓派官方的操作系统`Raspberry Pi OS`基于著名的`Debian Linux`开发，自带了丰富的工具软件，如`LibreOffice`，`Chromium`浏览器，甚至赠送了强大的商业软件也是世界三大数学/科学计算软件之一的`Mathematica`。满满的生产力！



**低能耗高性能ARM电脑**与**高可用性的开源设计软件**是非常鼓舞人心的两个趋势，

希望这期视频内容可以带大家管中窥豹，识别二维码即可前往B站观看。



视频内容

- 官方系统初始设置，国内软件源设置（若默认源更新较慢） 
- 常用命令行工具安装
  - ranger
  - aria2
  - you-get
- 设计软件安装
  - Blender， 令人难以置信的全功能3D创意套件，建模渲染动画剪辑全能型软件。
  - Gimp，图像处理，Adobe Photoshop替代者
  - Inkscape 矢量绘图，Adobe Illustrator替代者
  - QGIS，地理信息系统软件，ArcGIS替代者



