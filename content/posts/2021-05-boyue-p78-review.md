---
title: "Kindle坏了却重新找回阅读的快乐 - 博阅P78电纸书"
date: 2021-05-20T11:27:00+08:00
categories: ["blog"]
tags: ["Boyue","E-Reader"]
draft: false
---

前不久想看书，翻出泡面盖Kindle Paperwhite 1，背后的类肤材质涂层老化了，粘粘的，很是讨厌。找了瓶脱胶剂涂了涂，然后轻轻松松刮掉了厚厚一层脏兮兮的东西，强迫症那叫一个爽。然而，这货之后竟然触控屏失灵了，没了反应，嚯嚯，彻底挂了。

回想起来，这个Kindle还是2013年国行初上市的时候在亚马逊充的信仰，还买了官方皮套（前两年也裂开丢掉了）呵护它，竟然不知不觉用了7年有余。也算物尽其用了，是时候找个继任的阅读利器了。

去张大妈那里做了点功课，发现大家对开放系统（安卓）极尽赞美，其实很容易理解，Kindle这种基于Linux定制的封闭系统，怎么说呢，只看书非常称职。但是如果想浏览下网页，自带那个实验性浏览器根本不堪一用，又卡又慢，连鸡肋都比不上。想装常见的RSS新闻阅读器，没门。

如果给树莓派做显示器用呢，两个低功耗神器强强联合，岂不美哉！就这，还真有人做了，[Kindleberry](https://www.meccanismocomplesso.org/en/kindleberry-the-economic-ultraportable-laptop-with-kindle-and-raspberry-pi/)，原理就是先把Kindle越狱，然后安装一个终端模拟器`KTerm`，再用`ssh`连接到局域网内的树莓派，基本上就可以算是树莓派的无线电子纸显示器了，不过只能用命令行工具。算了，Kindle已挂，我就不折腾了。

说回博阅，作为张大妈社区和讨论区备受推崇的电纸书品牌，我竟然闻所未闻。没想到几年光景，这个市场已经发展得这么丰富多彩，而且博阅居然是老牌厂商了。刚好P78上市首发有优惠，值场老手们都在推荐，大屏的P10我又担心重量或者携带不便，就直接JD下单入手了。

![IMG_1625](https://tva1.sinaimg.cn/large/008i3skNgy1gqpatb9x5vj31400u07wj.jpg)

## ![IMG_1626](https://tva1.sinaimg.cn/large/008i3skNgy1gqpamnkuwjj31400u07wj.jpg)

## 外观

![IMG_1628](https://tva1.sinaimg.cn/large/008i3skNgy1gqpanuputjj30u0140kjn.jpg)

很快就收到了包裹，拆开一看包装平平淡淡，好在机身做工中规中矩，谈不上多精致，但也没有廉价感。

- 前面板：平面玻璃， check

- 后背材质；磨砂塑料，抗指纹抗老化，check

- 右侧配备MicroSD卡槽，这年头太少见了，本来自带存储已有32G了，这又支持最大扩展256G内存卡，存书存音乐什么的非常方便。check

- 屏幕素质，1872x1024分辨率，300PPI。7.8寸不大不小，很棒。check

- USB Type C 接口，check

- 底部居然有外放喇叭，音质尚可，挺方便。check

  



## 软件体验

基本上可以当做一个电子墨水屏的安卓平板用了。

- 安卓8.1的系统，算挺新的版本，够用且好用，check
- 设置里面可以启用Google Play，网络条件允许的情况下，百万APP任选。check
- 自带的APP基本都是必需的，书架（ Z-Reader，常见电子书格式几乎都支持了，TXT, CHM, FB2, MOBI, HTML, RTF, HTXT, EPUB, PDB, DOC, PRC, PDF, DJVU, ASW, PRC），浏览器，音乐播放器，文件管理器，词典。更新了系统还多了个悬浮球，一些操作不需要再去顶栏划，挺方便的。
- 屏幕刷新率比Kindle PW1快太多了，真是科技发展的红利。A2模式在做普通平板用的时候真是太好用了，浏览网页，RSS订阅，甚至视频都能以黑白色凑合看看。这里不禁让人想起贵到没朋友的大上科技的电子墨水显示器，博阅的A2模式可以勉力一战解个毒了。装个VNC viewer或者其他远程管理APP也能愉快的做个电脑显示器了，挺适合玩没显示器的树莓派。check
- 蓝牙5.0可以连耳机，我担心费电就没怎么用，也是个不错的加分项。check
- 支持安装字体，太棒了，思源宋体和思源黑体还自带了，但只有常规字重，其它字重下载了放在Fonts文件夹即可。check

![IMG_1732](https://tva1.sinaimg.cn/large/008i3skNgy1gqpaodpkamj31400u0kjn.jpg)

## 总结

我个人看`PDF`和`EPUB`格式的电子书比较多，另外就是每天都用RSS订阅APP（比如`Feedly`）看看新闻和资讯，再就是无意间发现的一款电子纸专用浏览器`EinkBro`，自带翻页手势，优化了排版，挺不错。接近一周的时间体现下来可以说是对博阅P78非常满意，也很欣喜，实在是比Kindle强太多了，最新的Kinlde Oasis没用过，不过即便屏幕素质高了，刷新快了，那个封闭系统想来也不过尔尔。

要说不足之处，开Wi-Fi上网电池似乎消耗挺快，感觉只能撑一天。不开Wi-Fi倒是和Kindle差不多了，一般看看书一周一充问题不大。[GoodEReader](https://goodereader.com/blog/reviews/boyue-likebook-p78-e-reader-review)评测里提到的没有WACOM感应层和笔记APP我也无感，因为不喜欢再拖根笔写写画画。

总的来说，P78让我重新找回了阅读的快乐，好物！

![IMG_1735](https://tva1.sinaimg.cn/large/008i3skNgy1gqpapfs2qkj30u0140b2b.jpg)