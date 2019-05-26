---
title: 网络架构-应用层
layout: post
category: 网络七层架构
date: '2019-05-25 18:30:00'
tags: internet
---

应用层为操作系统或网络应用程序提供访问网络服务的接口。应用层协议的代表包括：Telnet、FTP、HTTP、SNMP等。

## 1. 网络应用的规则
网络应用有很多，比如：email，视频对话，web，远距离登陆，Streaming Stored Video

### a) Client-Server
<img src="{{ '/assets/blog/application1.png' | prepend: site.baseurl }}" alt="">

客户-服务端，客户端就是你的电脑上面的一个客户端软件，比如腾讯QQ的登陆器；而服务端则是一个一直运行不关机的连着网络的电脑，比如VPS。

#### 客户端的特点
* 用于与客户端联系
* 不一定一直在线上
* 可以有不同的IP地址
* 主动建立联系的一方

#### 服务端的特点
* 总是在线上
* 通常有一个固定的IP地址
* 拥有一个数据中心，以防止数据丢失
* 等待的一方

### b) Peer-to-Peer(P2P)
<img src="{{ '/assets/blog/application2.png' | prepend: site.baseurl }}" alt="">

点对点，每一台电脑就是一个点，点对点就是跳过服务器，直接从一台终端电脑上获取资料，网上的Pt种子就是点对点，直接从一些个人电脑中获取资源的

#### P2P 特点
* 终端不总是在线上，不稳定
* 两个终端的IP地址都可能会发生变动，而且会间歇性的连接，这导致了很难去管理

## 2. 超文本传输协议(HTTP)
HTTP（HyperText Transfer Protocol）是网页应用层中最为广泛的一个网络协议，所有的WWW文件都必须遵守这个标准。而HTTP其实是一个客户端和服务器端请求和应答的标准。

### 流程
<img src="{{ '/assets/blog/application3.png' | prepend: site.baseurl }}" alt="">
* Iphone 用Safari打开浏览器，浏览器就发送HTTP 请求给Apache网页服务器
* 然后这个网页服务器里面存储着浏览器所需要的代码，然后就把这部分的代码发送HTTP回答给Iphone的浏览器
* 然后我们就看到了浏览器的内容了

### HTTP的基本格式
<img src="{{ '/assets/blog/application4.png' | prepend: site.baseurl }}" alt="">

### HTTP 回复状态code
* 200 -> OK 
	* 正常，没毛病
* 301 -> Moved Permanently
	* 你请求的内容已经被永久的移走了
* 400 -> Bad Request
	* 服务器看不懂你在请求啥
* 404 -> Page Not Found(最常看到的错误code)
* 505 -> HTTP Version Not Supported
	* 当你还在使用上世纪50年代的浏览器的时候，可能会出现这玩意

### 小饼干Cookies
Cookies 就是逛淘宝，上Youtube的时候，你不会想每次都输入一次用户名和密码，那有的人就很懒啦，就发明了Cookies。除了第一次打开淘宝外，以后每一次打开淘宝，它就会自动的把你的账号密码输进去，然后登陆，这就是Cookies

<img src="{{ '/assets/blog/application5.png' | prepend: site.baseurl }}" alt="How It Work">

### 网页缓存
网页缓存的概念就是，比方说我有一台服务器在美国，有两个中国的终端发送HTTP请求给我，让我把网页发过去，因为跨一个大洋洲，所以发送一次的成本很高且延迟大。假如不是两台电脑请求，而是几百上千台请求，这样我的服务器就很容易挂掉了。

<img src="{{ '/assets/blog/application6.png' | prepend: site.baseurl }}" alt="How It Work">

为了解决这个问题，我有一个中国的代理服务器，当有电脑要发HTTP请求给我的时候，中国的代理服务器先看看我里面有没有你要的东西，如果没有的话，再像美国服务器请求，然后把资料缓存到本地。当再有一台电脑发送HTTP请求的时候，中国的代理服务器就把之前缓存好的资料直接发给它。



## 3. 远程安全登陆(SSH)
SSH(Secure Remote Login) 是你从一台电脑远程登陆进另外一台电脑的方法，有很强的加密性，占用了22端口

SFTP(SSH File Transfer Protocool)是现阶段最广泛使用的文件传输协议


## 4. 电子邮件


## 5. DNS


## 6. P2P 应用

## 7. 端口