---
title: 网络架构-应用层
layout: post
category: 网络七层架构
date: '2019-05-29 18:30:00'
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
HTTP（HyperText Transfer Protocol）是网页应用层中最为广泛的一个网络协议，所有的WWW文件都必须遵守这个标准。而HTTP其实是一个客户端和服务器端请求和应答的标准，占用80端口。

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

Cookies的用途很广泛：
1. 授权
2. 网页购物车
3. 购物建议

### 网页缓存
网页缓存的概念就是，比方说我有一台服务器在美国，有两个中国的终端发送HTTP请求给我，让我把网页发过去，因为跨一个大洋洲，所以发送一次的成本很高且延迟大。假如不是两台电脑请求，而是几百上千台请求，这样我的服务器就很容易挂掉了。

<img src="{{ '/assets/blog/application6.png' | prepend: site.baseurl }}" alt="How It Work">

为了解决这个问题，我有一个中国的代理服务器，当有电脑要发HTTP请求给我的时候，中国的代理服务器先看看我里面有没有你要的东西，如果没有的话，再像美国服务器请求，然后把资料缓存到本地。当再有一台电脑发送HTTP请求的时候，中国的代理服务器就把之前缓存好的资料直接发给它。



## 3. 远程安全登陆(SSH)
SSH(Secure Remote Login) 是你从一台电脑远程登陆进另外一台电脑的方法，有很强的加密性，默认占用了**22端口**，推荐使用Putty

<img src="{{ '/assets/blog/application8.png' | prepend: site.baseurl }}" alt="How It Work">

SSH文件传输协议，叫SFTP(SSH File Transfer Protocool)是现阶段最广泛使用的文件传输协议，推荐使用WinSCP

## 5. 域名服务器DNS
因为每一个IP地址是32bit（假设都是IPv4）用来记录网站的地点，但是一串数字的IP地址对于人类来说很难记录下来，所以我们有了域名，来把IP地址抽象化使得人类容易记得，比如www.google.com 的IP地址是172.217.164.196。

域名系统，叫DNS（Domain Name System），是进行域名(domain name)和与之相对应的IP地址 (IP address)转换的服务器。DNS中保存了一张域名(domain name)和与之相对应的IP地址 (IP address)的表，以解析消息的域名。 

### 域名是怎么工作的
<img src="{{ '/assets/blog/application7.png' | prepend: site.baseurl }}" alt="How It Work">

比如上面这幅图，如果有人第一次搜索"www.amazon.com" 这个域名
* 首先，会先到根域名服务器，就是*.*，去找*.com.*
* 然后，找*.com.*域名服务器，去找*amazon.com.*
* 最后，找*amazon.com.*域名服务器，找到了*www.amazon.com.* ，上面记录了这个域名的对应IP地址，就可以访问这个网站了。

### 顶级域名，权威域名

顶级域名，叫TLD（Top-Level Domain）比如说：**.com, .org, .net**这些都是顶级域名

权威域名，是被组织or服务器提供者维持的，对下面的域名“说了算”，可以对其区域内的域名进行设置，修改和删除

### DNS服务器

<img src="{{ '/assets/blog/application9.png' | prepend: site.baseurl }}" alt="How It Work">

下面一步一步解释本地DNS怎么工作：

1. 我第一层，我要登陆Baidu.com，但是我的火狐浏览器找不到这个baidu IP地址，所以我发送一个Query（查询）给本地DNS服务器
2. 本地DNS服务器发现，“哎，我也没有baidu IP地址，然后他就会发送一个Query给root DNS服务器
3. root DNS服务器虽然不知道baidu IP具体地址，但是它置顶baidu.com 的TLD，就是知道.com的地址
4. 本地DNS服务器就又发一个Query给.com这个TLD DNS服务器，问他baidu IP地址是什么
5. .com TLD DNS 服务器也不知道具体的baidu.com IP地址，但是知道它的权威服务器地址
6. 本地DNS服务器就又又发了一个Query给baidu的权威服务器，因为权威服务器是知道它领域里所以域名的IP地址，这时候终于得到了baidu IP地址
7. 权威服务器把baidu.com 的IP地址发过去给本地DNS服务器
8. 本地DNS服务器把IP地址发回来给我，然后我就能登陆baidu.com了✌

**如果每次上一个网站都这么麻烦，岂不是网速都变龟速了？**所以本地DNS服务器的作用就在于此！！

因为不仅仅是只有一个人使用本地DNS服务器，当很多人一起使用的时候，比如我登上百度，你也登百度，那本地DNS服务器就把baidu.com的IP地址缓存起来，当又有人问baidu.com的IP地址时，直接把地址给他，就可以不用每次都一个一个Query！！！✌

### DNS的record

**type = A**
* 存储IP地址，只适用于IPv4
* 名字是  hostname

**type = AAAA**
* 跟Type A 差不多，不过是适用于IPv6

**type = CNAME**
* 创造一个可以替代的record给另外一个record
* 比如说，lij.jir.baidu.com我每次登陆都要输入这么多就很烦，所以我弄一个别名给这个www.jiadong.work 就可登陆上面的一长串网址

**type = MX**
* 用于邮箱，具体没用过
* value is name of mailserver associated with name

## 6. P2P 应用

### 纯P2P结构
* 没有24小时开机的服务器
* 任意端系统直接获得联系
* peer是间歇性连接的，而且会改变IP地址

是P2P应用的例子，比如Pt种子，Skype和Streaming

### P2P 文件传输，BitTorrent
* 一个文件会被拆分成256Kb 的块，叫做Chunks
* Peers 会发送/接受这些chunks

下载文件为什么越多人下载，速度越快呢？
```
比如说一个文件可以分成10份，1个人1小时可以拉1份的Chunk

如果只有一个人在拉这个文件的时候，那么我要花10小时才能下载好

如果有两个人同时拉这个文件，我拉1，3，5，7，9另一个人拉2，4，6，8，10，而且拉的时候，我把我下载好的文件同时发给你，这样就相当于一个人以两倍的速度下载！当然，下载速度不可能无上限快的，它受限于很多条件，比如你的缓存，带宽等等
```

## 7. CDN
当你看视频的时候，有没有想过一个在线视频有多大？以一个1小时左右的影片，720画质最少也得500-800M，而这样的一部影片每次都要从源头下载下来，然后你还不一定全看完！

为了解决如果使得成百上千的用户都可以很爽的看视频！诞生了CDN的概念，Content Distribution Networks，存储很多影片的copy在不同的地理分布地区。比如，我在北京看影片，我就从北京附件的CDNs那里获取影片。。

那么用户是怎么获得影片的呢？？

<img src="{{ '/assets/blog/application10.png' | prepend: site.baseurl }}" alt="How It Work">

### DASH

DASH: Dynamic, Adaptive Streaming over HTTP
简单来说就是把文件切成小块，然后通过HTTP协议来传输