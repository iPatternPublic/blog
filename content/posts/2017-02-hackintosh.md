---
title: "Hackintosh on Two PCs"
author: "iPattern"
date: 2017-02-09T16:33:25+08:00
description: "This is meta description"
categories: ["Experiment"]
tags: ["Experiment"]
---

Just installed Hackintosh on two types of desktop PCs with tonymacx86’s guide, and they worked perfectly, even iMessage and FaceTime ran flawlessly.

Here are the main steps and the hardware list:

## Main Steps

1 Make a usb installer with Unibeast on Windows Vmvare EI Captain
2 Change BOIS settings
3 Install Mac OS Sierra on PC
4 Install drivers with MultiBeast on the Hackintosh
5 Install latest Nvidia Web Driver
6 Troubleshooting and Optimizations

## TYPE 1

> ASUS Z97K R2.0/Intel i7 4790/Nvidia GTX750

|Parts | Type|
| ------------- |:-------------:| -----:|
| Motherboard |	ASUS Z97K R2.0|
| CPU |	Intel i7 4790|
| GPU |	Nvidia GTX750|
| Memory |	Kingston DDR3 1600 MHz 8G*2|
| SSD |	Samsung SSD 750 EVO 120GB|

### Troubleshooting

- Fix Nvidia Web Graphics Driver with Clover Configurator 

EFI -> config.plist -> NVIDIA -> `true`

- Enable TRIM in Terminal 

`sudo trimforce enable`

## TYPE 2

> ASUS B85-PRO GAMER / Intel i7 4790 / Nvidia GTX970

| Parts	| Type|
| ------------- |:-------------:| -----:|
| Motherboard |	ASUS B85-PRO GAMER BOIS Version:0003|
| CPU |	Intel i7 4790|
| GPU |	Nvidia GTX970|
| Memory |	Kingston DDR3 1600 MHz 8G + Samsung DDR3 1600 MHz 8G|
| SSD |	LITEON IT LCH-128V2S 120GB|

### BOIS Settings

1. VT-d : disable 
2. IO Serial Port: Disable 
3. Intel xHCI Mode: Auto 
4. EHCI Hand-off: Enable 
5. Secure Boot -> OS Type: Other OS

### MultiBeast Settings:

1. Audio: Realtek ALC 1150 
2. Network: Intel-> Apple Intel E1000ev3.3 
3. USB: 8 Serials USB Support

### Troubleshooting

- Audio Realtek ALC 1150 no sound after sleep 

Install this kext from tonymacx86 using KextBeast: ready-made kext for 1150 on Gigabyte GA-Z79MX-gaming 5 and similar motherboards. 

- Restart after Sleep 
Still not sure what exactly the problem is, after formating the extra HDD from NTFS to Journaled HFS+, it rarely happened.

- Enable TRIM in Terminal 
`sudo trimforce enable`

————————————————

[博客搬家](https://blog.csdn.net/dxbjfu08/article/details/54631866)