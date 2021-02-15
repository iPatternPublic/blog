+++
title = "Raspberry Pi 4用作Home Server"
image = "/images/post/post-1.jpg"
author = "iPattern"
date = 2019-11-07T05:00:00Z
description = "This is meta description"
categories = ["编程 Programming"]
type = "post"

+++

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

参考链接：
- [Raspberry Pi 4 VNC Remote Connection Desktop Error - Raspberry Pi Stack Exchange](https://raspberrypi.stackexchange.com/questions/101796/raspberry-pi-4-vnc-remote-connection-desktop-error)
- [Build a Samba file server](https://magpi.raspberrypi.org/articles/raspberry-pi-samba-file-server)