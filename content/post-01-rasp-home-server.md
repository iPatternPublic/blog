+++
title = "树莓派4折腾记"
image = "/images/post/post-1.jpg"
author = "iPattern"
date = 2021-02-16T04:30:00+08:00
description = "This is meta description"
categories = ["编程 Programming"]
type = "post"

+++
## Desktop篇
树莓派4刚出来的时候，官方宣称它是一个功能完备的Desktop PC。
所言非虚。

### Raspberry Pi OS
似乎在树莓派4这一代，官方系统Rasbian也改名Raspberry Pi OS了，甚至还有了x86版，当然因为授权问题，阉割了Mathematica。
不太理解他们推出x86版本的意义，话说回来ARM的64位正式版支持迟迟未推出反倒令人着急。
好在USB启动支持做得更方便了，用Raspberry Pi Imager刷入bootloader EEPROM到microSD卡，插卡通电，
等树莓派指示灯绿灯闪烁，或外接显示器全绿色，即可完成升级。


树莓派4用了半年的OpenWRT系统，源自GitHub上的`OpenWrt-Rpi`项目的`openwrt-bcm27xx-bcm2711-rpi-4-ext4-sysupgrade.img.gz`固件。
各类插件非常齐全，半年使用下来也非常稳定，似乎未出现过故障，体验堪比前年使用的3215u的x86软路由了。
只可惜树莓派只有一个网口，做主路由多有不便，只好拿来做旁路由。另外用USB3拖个移动硬盘也稍微凌乱了些。

可惜的是它的smb共享很古怪，我一直没搞定，然后偶尔固件总是莫名其妙提示有些未保存的配置，最近有时间，也许是时候换个系统了。。。

俺首先考虑的是Open Media Vault，可惜检索到需要先刷Raspberry Pi OS Lite，然后通过git安装OMV5测试版。
大量文件git + 测试版，这两项足以劝退了。。。

然后是令人心动的ESXi，这也是俺当初在3215u上使用的系统，体验优秀，稳如磐石。有消息它已经放出树莓派4的测试版固件了，可惜还要再等。

百无聊赖，想起来官方系统，依然是最稳的树莓派系统，便利的VNC，豪奢的免费Mathemetica，没有Vulkan驱动搞不定2.8前依然堪用的Blender2.79...
不争气的口水从眼角流下，2.8G的`Raspberry Pi OS with desktop and recommended software`用torrent拖下来开刷。

### VNC 配置
虽然ssh管理树莓派轻量便捷，但还是免不了个别情形下需要使用树莓派的桌面系统，或是使用一些窗口软件。
在不连接显示器的情况下，VNC viewer连接树莓派ip：`10.0.0.5`，默认用户名：`pi`，
会提示错误: **cannot currently show the desktop**
可先用ssh链接`ssh pi@10.0.0.5`，输入密码，然后运行`raspi-config`，在出现的配置选项找到`Display Option`然后`Resolution`，指定一个分辨率即可。（如1920*1080 60Hz）
完成后按提示重启，即可生效。
### exFAT硬盘格式支持
估计是由于Linux内核版本太低的缘故，树莓派的Raspberry Pi OS不能直接加载exFAT格式的外置硬盘，我当前使用的内核版本为`Kernel: 5.4.83-v7l+`。
按照检索到的方法安装下面两个包即可。
```bash
sudo apt-get install exfat-fuse
sudo apt-get install exfat-utils
```
### smb共享配置
说来惭愧，之前在树莓派的OpenWRT上一直没搞定smb共享文件夹，网上搜到的配置比较混乱，好些似乎因为版本过时不起作用。
好在这次找到了一个非常简单的配置方法，也不需要给树莓派静态ip，共享目录为挂载移动存储的目录`/home/pi/shared`。
安装以下两个包
```bash
sudo apt-get install samba samba-common-bin
```
然后sudo编辑smb配置文件
```bash
sudo nano /etc/samba/smb.conf
```
末尾加上
```conf
[share]
    path = /home/pi/shared
    available = yes
    valid users = pi
    read only = no
    browsable = yes
    public = yes
    writable = yes
```
测试参数是否正确
```bash
testparm
```

设置`pi`账户密码
```bash
sudo smbpasswd -a pi
```
重启 Samba server:
```bash
sudo service smbd restart
```

默认smb服务名称`RASPBERRYPI`，可在Mac，PC，Linux的文件浏览器的网络内发现。

### Manjaro Sway
除官方系统外，俺用的最久最爽的一个。
### Manjaro KDE
界面繁复，pacman和AUR清爽。
### Ubuntu Desktop 20.10
界面华丽但对树莓派4显得沉重了些，卡顿明显。
## Server篇
Ubuntu Server 20.04
## 游戏篇
### RetroPie

- Wolfanoz_Nostalgia_64GB_RPi4_Official
- [256gb]-Epic.Noir.RPi4.4.6.8-RickDangerous



###### 参考链接：

- [OpenWrt-Rpi](https://github.com/SuLingGG/OpenWrt-Rpi)
- [Raspberry Pi 4 VNC Remote Connection Desktop Error - Raspberry Pi Stack Exchange](https://raspberrypi.stackexchange.com/questions/101796/raspberry-pi-4-vnc-remote-connection-desktop-error)

- [Build a Samba file server](https://magpi.raspberrypi.org/articles/raspberry-pi-samba-file-server)

- [Build a Raspberry Pi 4 NAS with Open Media Vault 5](https://linuxhint.com/raspberry_pi_open_media_vault/)