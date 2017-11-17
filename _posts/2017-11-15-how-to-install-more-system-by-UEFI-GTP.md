---
layout: post
title: "如何在UEFI模式下使用GTP分区格式安装多系统"
subtitle: "ubuntu16.10,win10"
author: "刘华"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - ubuntu
---

> This docuemnt is not completed and will be updated anytime.

## Catagory

1. [Materials](#Materials)
	1. [Download_Ubuntu16.04](#Download_Ubuntu16.04)
	2. [Download_Win10](#Download_Win10)
2. [install](#install)
	1. [first_install_ubuntu16.04](#first_install_ubuntu16.04)
	2. [two_install_win10](#two_install_win10)
3. [相关查询资料](#相关查询资料)

---

## Materials

[ubuntu16.04下载地址](https://www.ubuntu.com/download/alternative-downloads) 
[Win10下载地址](https://www.microsoft.com/zh-cn/software-download/windows10ISO)

## install

> set system use UEFI

![UEFI set at  BIOS](/img/uefi.png)

- #### first_install_ubuntu16.04
先制作一个系统安装盘(u盘或镜像光盘),设置相应启动项,进入try install 安装界面，手动格式化磁盘为gtp格式。
点击install ubuntu16.04,选择设置手动分区.
1.first Creating an EFI System Partition(uefi 必要分区,holds EFI-mode boot loaders and related files)
2.创建其他分区

- #### two_install_win10
先制作系统安装盘(u盘或镜像光盘),设置相应启动项，分区时在控盘空间进行分区，即可，安装完成在uefi启动顺序中使用ubuntu启动，进入执行命令 update-grube




## 相关查询资料
[what is UEFI](http://whatis.techtarget.com/definition/Unified-Extensible-Firmware-Interface-UEFI)<br>
[ubuntu how to install on UEFI](https://help.ubuntu.com/community/UEFI)<br>
[what is gtp](https://www.partition-tool.com/resource/GPT-disk-partition-manager/partition-gpt-disk.htm)


