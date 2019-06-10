---
title: 使用密钥登录Linux服务器-生成SSH key
layout: post
date: '2019-06-01 00:30:00'
category: Putty
tag: ssh putty
---

程序员平时跟Linux服务器少不了打交道，大多数Windows用户会选择
PuTTY 这这款软件，我们以这款软件为例，说明一下如何生成SSH密钥对，使用这个密钥去登录服务器，省去了输入密码的麻烦。

首先，我们下载PuTTY这个软件，请注意的是，很多网站上提供的软件是仅仅包含PuTTY单个软件的，但是全套包括
putty.exe, puttygen.exe, psftp.exe, pscp.exe, pagent.exe.

这五款软件，今天我们介绍puttygen.exe的使用方法

请去官方下载此软件，以保证文件完整性，同时下方有搬运。网速不好的同学可以从下方下载。或者可以单独下载这个软件，反正基本是一次性使用。

[puttygen单文件免安装][download1]

[putty-64bit-0.70-installer][download2]

经过了无脑的安装之后，你就可以从开始菜单中搜索 PuttyGen找到这个程序了

<img src="{{ '/assets/blog/ssh-1.jpg' | prepend: site.baseurl }}" alt="">

打开之后长这样

<img src="{{ '/assets/blog/ssh-2.jpg' | prepend: site.baseurl }}" alt="">

首先我们选择菜单栏中的 key -> SSH-2 RSA key

<img src="{{ '/assets/blog/ssh-3.jpg' | prepend: site.baseurl }}" alt="">

然后其他参数保持默认，即下方种类为 RSA，位数为2048，按下红色箭头所指向的Generate就可以了，然后就会有一个进度条出现，在蓝色框区域随机的晃动鼠标，以产生一些随机的东西用来生成密钥

<img src="{{ '/assets/blog/ssh-4.jpg' | prepend: site.baseurl }}" alt="">

如果移动鼠标够快，很快我们就得到了一个Key，这时候软件里显示出来的就是公匙。

<img src="{{ '/assets/blog/ssh-5.jpg' | prepend: site.baseurl }}" alt="">

在Key comment这一栏可以输入一个你想要的名字，可以识别不同的key，对功能没有什么影响，只要随便输入一个就好了

下面是key passphrase, 就是这个密钥对的密码，如果你想输入就输入，但是输入后每次登陆就需要输入这个密码，就无法实现我们无密码登陆服务器的初衷了。

所以下面两个框框留白，我们点击下面的 Save private key

<img src="{{ '/assets/blog/ssh-6.jpg' | prepend: site.baseurl }}" alt="">

软件会警告你没有输入passphrase， 是否要继续，我们点击是就好了

然后我们选择一个保存位置，保存下私匙。软件里上面那个框框显示的内容就是公匙，我们把他全部复制下来，在后面备用

---

私匙是自己留着的，一定要保证他的安全，有私匙就可以登录你的服务器，公匙是上传到服务器上的，用来验证身份

我们登录到服务器，不管你用什么方法，登陆上去。然后在家目录下面 新建一个文件夹 叫 .ssh 注意前面的小点，这代表这个文件夹是隐藏的， 使用ls 无法查看， 需要 ls -a, 然后进入到这个文件夹

```
cd ~
mkdir .ssh
cd .ssh
```

之后，我们新建一个文件，叫做 authorized_keys 将刚才复制的公匙粘贴进去，皆可以了，这时候我们就完成了公匙的安装，这一步需要会使用文本编辑器，vi， nano等，如果不会，可以使用echo命令

```
echo "你刚才复制的东西" > authorized_keys
```

输入 ls 命令应该会显示有个authorized_keys文件在你的~/.ssh 目录下

<img src="{{ '/assets/blog/ssh-7.jpg' | prepend: site.baseurl }}" alt="">

文件里面的内容是你刚才生成出来的 Public Key

<img src="{{ '/assets/blog/ssh-8.jpg' | prepend: site.baseurl }}" alt="">

最后一步是使用Putty导入私匙进行连接

我们打开Putty，先输入你的服务器连接信息之后，保存下这个会话

一定要 用户名@主机名 的方式进行保存，这样才能真正的免密码登录。

一般为 root@你的IP

然后再左侧切换到Connection -> SSH -> Auth 选项卡

我们选择上我们刚才保存的私匙。

<img src="{{ '/assets/blog/ssh-10.jpg' | prepend: site.baseurl }}" alt="">

选择上这个私匙之后，私匙的保存位置不要更改，否则需要重复此步骤重新选择。然后切换回Session选项卡，点击Save， 保存下这个操作，否则下次还需要重新选择私匙位置

这时候我们就完成了私匙的部分，全部步骤完成。我们这时候选择了服务器之后，点击Open，应该就可以提示成功使用了 SSH Key 登录

<img src="{{ '/assets/blog/ssh-11.jpg' | prepend: site.baseurl }}" alt="">

使用SSH key 登录Linux服务器的步骤就此完成，以后既可以通过双击Putty里面的保存的会话来快速无密码访问到服务器。

注意事项：

1. 请注意不要让别人在你的服务器上安装公匙，如果你自己没发现的话，别人就可以随时登录你的服务器，改了密码也没用

2. 私匙要保存好，那就是打开你服务器的钥匙，如果泄露，请重新生成一对，然后替换到服务器里的那个公匙

3. 如果服务器拒绝了这个私匙，多半是公匙没有正确导入，请确保路径和文件名正确。

4. 如有留言，请移步到[UW第一帅王志远的博客][wzydale]!


[download1]:https://blog.wzydale.com/wp-content/uploads/2019/02/puttygen.zip

[download2]:https://blog.wzydale.com/wp-content/uploads/2019/02/putty-64bit-0.70-installer.zip

[wzydale]:https://blog.wzydale.com/create-ssh-key/