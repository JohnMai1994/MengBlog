---
title: 如何在Window10的命令提示符（Terminal）中使用Linux Bash命令
layout: post
date: '2019-05-06 13:57:43'
category: Jekyll搭建
tags: Window10, Bash
New field 4:
  New field 6: ''
---

熟悉Linux系统的童鞋们，当使用Window 10的Terminal时，发现```ls```不能用，```vi```不能用，还有```cd```的用法也不一样了，肯定是会相当崩溃吧！今天Meng演示如何在Window 10 的 Terminal 中使用bash（P.S. 这个方法只适用于Window 10版本以上）。

### Step 1 **开启Win10开发人员模式**

* 在```开始```的设置 -> 更新和安全 -> 针对开发人员中选择“开发人员模式”，点击后会下载“开发人员模式包”

![tu1](https://i.ibb.co/L8nZq5P/Snipaste-2019-05-06-14-24-05.png)

![tu2](https://i.ibb.co/fxQGz4B/Snipaste-2019-05-06-14-24-26.png)

* 也可以```开始```搜索“开发者选项设置”，考到“开发者选项”后，点击“开发人员模式包”

![tu3](https://img.ithome.com/newsuploadfiles/2016/6/20160615_092530_663.png)

### Step 2 **勾选Linux的Win10 子系统(Beta)**

* 进入```开始```搜索“控制面板” -> 程序和功能 -> 启动或关闭Windows功能，找到“适用于Linux的Windows子系统(Beta)，点击“确定”后安装。

![tu4](https://img.ithome.com/newsuploadfiles/2016/6/20160615_093425_851.png)

### Step 3 **更新&升级**

* 重启后，打开window terminal后，输入```bash```进入Linux Bash模式，然后输入：

```
sudo apt update
sudo apt upgrade
```
* 进行升级。。

### Step 4 **享受Bash的快感吧**

* 至此，安装已完成，可以安装其他工具配置开发环境，谢谢阅读观看。