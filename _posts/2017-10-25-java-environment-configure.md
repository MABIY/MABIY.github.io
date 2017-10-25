---
layout:	post
title:	"java environment configure"
subtitle:	"with ubuntu"
author:	"刘华"
header-img: "img/post-bg-unix-linux.jpg"
tags:
    - java
    - linux
---
> This document is not completed and will be updated anytime.

## 使用ubuntu
> ubuntu 版本信息:16.04 desktop gnome 3.18.5 

## Catqgory

1. [安装jdk](#安装jdk)
	1. [下载jdk](#下载jdk)
	2. [手动编辑环境变量配置jdk](#手动编辑环境变量配置jdk)
	3. [update-alternatives-配置多版本jdk](#update-alternatives-配置多版本jdk)
2. [参考](#参考)

---

## 安装jdk

- #### 下载jdk
[下载地址jdk8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) | [下载地址jdk7](http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html)

- #### 手动编辑环境变量配置jdk

  有3个地方可以配置  
    /etc/profile  
    /etc/environment  
    ~/.bashrc  
  在/etc/environment配置的环境变量:
  
  ```bash
  export JAVA_HOME=/usr/local/jdk1.8.0_91
  export CLASSPATH=..:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/local/jdk1.8.0_91/bin"
  ```
  在ternimal中临时生效，永久生效需要reboot computer
  
  ```shell
  source /etc/environment
  java -version
  ```
- #### update-alternatives-配置多版本jdk
  首先需要靠update-alternatives工具命令实现，原理是通过生成相应版本的软链接.  
  <br/>    
  ```shell
  //查询当前jdk 配置
  sudo update-alternatives --display java
  ```
  ![](/img/display_java.png)
  我自己装了2个版本
  ```bash
  /usr/local/jdk1.7.0_60/bin/java - priority 300
  /usr/local/jdk1.8.0_91/bin/java - priority 300
  ```
  openjdk 系统自己装的。

  发现jdk位置不应该在这里 mv /usr/local/jdk* /usr/bin/ (移动位置)
  
  新配置jdk环境
  首先删除之前jdk 环境配置
  ```bash
  sudo update-alternatives --remove java /usr/local/jdk1.8.0_91/bin/java
  sudo update-alternatives --remove javac /usr/local/jdk1.8.0_91/bin/javac
  sudo update-alternatives --remove java /usr/local/jdk1.7.0_60/bin/java
  sudo update-alternatives --remove javac /usr/local/jdk1.7.0_60/bin/javac
  ```
  重新配置jdk 到alternatives工具  
  ```bash
  sudo update-alternatives --install /usr/bin/java java /usr/bin/jdk1.8.0_91/bin/java 300
  sudo update-alternatives --install /usr/bin/javac javac /usr/bin/jdk1.8.0_91/bin/javac 300
  sudo update-alternatives --install /usr/bin/java java /usr/bin/jdk1.7.0_60/bin/java 300
  sudo update-alternatives --install /usr/bin/javac javac /usr/bin/jdk1.7.0_60/bin/javac 300
  ```
  **查看配置结果**
  ![](/img/jdk_configure.png)

  手动切换java javac版本
  ```shell
   sudo update-alternatives --config java
   sudo update-alternatives --config javac
  ```
- #### 参考
   [update-alternatives](https://linux.die.net/man/8/update-alternatives)
