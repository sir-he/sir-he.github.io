---
layout: post
keyword: "sir-he,sir 何,sir-he blog,shadowsocks,shadowsocks 使用"
title:  "shadowsocks的正确使用姿势"
date:   2017-10-25
---

## 基础篇

### 1、下载shadowsocks，地址：[https://github.com/shadowsocks/shadowsocks-windows/releases/download/2.5.8/Shadowsocks-2.5.8.zip](https://github.com/shadowsocks/shadowsocks-windows/releases/download/2.5.8/Shadowsocks-2.5.8.zip)，我这里直接用这个地址下载失败，可以通过[http://lyxz.gq](http://lyxz.gq)来中转

### 2、解压Shadowsocks-2.5.8.zip，得到Shadowsocks.exe，右键以管理员身份运行。
### 3、打开[http://www.ishadowsocks.com/#free](http://www.ishadowsocks.com/#free)获得账号密码（或者使用自己的），这里得到账号如下：

服务器地址:US1.ISS.TF 端口:8989 密码:08757213 加密方式:AES-256-CFB

<!--more-->

### 4、将得到的ss账号填入Shadowsocks.exe，如图，然后点击确定

![this-one][this-one]

### 5、到屏幕右下角找到灰色小飞机图标，右键，如图

![this-two][this-two]

### 6、点击启动系统代理，然后就可以开始自由上网了。

## 高级篇

既然是shadowsocks的正确使用姿势，仅有基础篇肯定是不够的，下面是高级篇
### 1、基础知识普及：
系统代理模式->PAC模式：pac模式也就是智能模式，这个模式可以让被墙的网站走ss，而没被墙的不走ss，这样就不影响本来的网速。
系统代理模式->全局模式：这个也就是让访问所有的网站都走ss，有时pac不够精确，被墙了的网站，没有走到ss，就需要启用这个模式了，但是如果一直使用这个模式，会影响自己的网速的。

服务器->编辑服务器：这个就是进入到添加ss账号的界面，这里添加后就可以记录多个账号，当有多个账号时，哪个账号前有勾，就说明使用的哪个，点击一下其他的账号，就启用其他账号了，添加服务器界面下面的1080端口，是指ss绑定哪个本地端口，这个值可以随便改的，但是不能是已经被其他程序占用了的，怎么看是否被占用，请在命令行中输入netstat -ano。

开机启动：看名字就懂了，就是开机后不用手工运行这软件了，自己就会启动。

允许来自局域网的连接：如果你有安卓手机，或者局域网中其他设备需要使用你的ss账号，就需要勾上这个了。

### 2、安卓设备通过电脑上的ss实现翻墙：
* 将手机和电脑连接到同一局域网。
* 在wifi的高级选项中，有个代理选项，打开那项，主机名输入电脑ip（命令行中输入ipconfig可以看到ip），端口输入8123（固定的，就是8123），如图，然后确定。

![this-three][this-three]

* 电脑上ss小飞机右键勾上允许来自局域网的连接，然后就可以手机自由上网了。

注：弱弱的说下，这样搞的就不需要root权限，另外苹果手机也可以用这个方法翻墙。

### 3、QQ使用ss上网：

* 打开QQ客户端，点击右上角向下的三角形，弹出如图界面。

![this-four][this-four]

* 类型选择sock5代理，地址输入127.0.0.1（如果ss是安装在其他电脑上，就输入那台电脑的ip），端口输入1080，这里的1080需要和前面的添加服务器界面的1080一样，如果前面你修改为了其他端口，就需要把此处也修改为和前面一样的端口。

* 点击确定，开始登陆QQ吧。

小提示：
勾上允许来自局域网的连接，其实就是对外提供了代理

8123端口，就是http代理的端口

1080端口，就是sock5代理的端口

ss给我们提供的就是sock5代理，然后使用了ss_privoxy把sock5代理转换为了http代理，懂了这个原理后，后面的很多东西就可以自己DIY了。


[this-one]:    {{site.url}}/assets/use_shadowsocks1.png
[this-two]:    {{site.url}}/assets/use_shadowsocks2.png
[this-three]:    {{site.url}}/assets/use_shadowsocks3.png
[this-four]:    {{site.url}}/assets/use_shadowsocks4.png