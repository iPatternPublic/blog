---
title: "Fedora21安装Broadcom无线网卡驱动"
author: "iPattern"
date: 2015-03-10T19:48:30+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["Linux"]
---

前两天在旧笔记本上安装了Fedora 21 workstation 32位版本，装好发现无线网卡不能使用（Fedora节操高），网上查了查，在fedora论坛找到了解决办法。

原文链接： [点击打开链接](http://forums.fedoraforum.org/showthread.php?t=239922)

分三步：

## Step 1: Identify the chipset of the wireless device

第一步：识别无线网卡型号，终端运行：lspci



我的本反馈最后一行为 10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
即无线网卡型号为 BCM4312


## Step 2: Choose the right driver

第二步：选择合适的驱动，原文给的选择表如下：（我懒的看完就选了version 4那个，然后就成功了。。）

                           lspci
                                         |
                                Any of these listed?
                                        4301
                                        4303
                                        4306
                                        4309
                                        4311
                                        4312
                                        4318
                                       /    \
                                      /      \
                                     /        \
                                    /          \
                                  Yes           No
                                  /              \
                                 /                \
                                /                  \
                             lsmod                4310?
                              /                   /   \
                             /                   /     \
                            /                  Yes      No
                          b43                  /         \
                        loaded?               /          43XG
                        /    \           ndiswrapper   4313,43224
                       /      No                        4321,43225
                      /        \                         4322,43227
                     /          \                         4328,43228
                   Yes       b43legacy                      /   \
                   /          loaded?                      /     \
                  /           /     \                    Yes      No
                 /          Yes      No                  /         \
                /           /         \                 /           \
             4306?         /           \          broadcom-wl      4320?
            4311?      Install        4311?                     (from lsusb
           4318?      version 3        4312?                   or other means)
           /   \      firmware         /   \                        /    \
          /     \                     /     \                      /      \
        Yes      No                 Yes      No                  Yes       No
        /         \                 /         \                  /          \
       /           \               /           \                /            \
b43-openfwwf     Install     broadcom-wl   ndiswrapper    b43-openfwwf   ndiswrapper
    or          version 4                                       or
  Install       firmware                                    rndis_wlan
 version 4
 firmware

## Step 3: Install the driver
第三步：安装驱动

Install b43-fwcutter. This is the software package that does the extraction of the firmware from the proprietary driver.安装b43-fwcutter，这个软件包是用来解压缩后面的驱动固件的。
Code:

```bash
su
yum install b43-fwcutter
```
Determine which native driver is being used by the wireless card (b43 or b43legacy). The kernel is generally good about detecting a Broadcom wireless card and loading the correct driver module for it. The following terminal command will list the loaded kernel modules in alphabetical order. Look for b43 or b43legacy.检测无线网卡使用的驱动，命令行给出的列表是按字母顺序来的，注意查找B43或B43legacy（英语一般，大致这么翻译吧。。）
Code:
`lsmod | sort`
Do this step only if you need to install version 4 firmware for the b43 driver module. Copy and execute the following command lines one after the other in a Fedora terminal.这是给b43驱动安装version 4固件的code，终端执行即可。
Code:

```bash
wget http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver	
su
b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```
后面还有其他版本驱动的安装说明，我没用到就不翻了，原帖有详细说明。 

[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/44179825)