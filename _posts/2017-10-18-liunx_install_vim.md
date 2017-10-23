---
layout: post
keyword: "sir-he,sir-he blog,vim安装,linux,linux下vim安装,centos"
title:  "linux下vim安装"
date:   2017-10-18 11:37:09
---

本文以centos7为讲解：

我们安装完Centos后，它默认是安装了Vi编辑器的。但Vim编辑器是没安装或者未完全安装的。 

下面进行安装配置：

第一步：登录 linux 系统

第二步：在命令行敲入“vi”后按"tab"键，可以看到目前系统中只安装了vi

![linux_vim0.png][linux_vim0.png]

<!--more-->

第三步：如果缺少vim，进行安装：

>yum -y install vim*

![linux_vim1.png][linux_vim1.png]

刚安装的VIM，可能界面并不是十分友好，这就需要我们去更改vim的配置文件，按照我们的需求去修改它。设置 Vim编辑环境 配置 有两种方式：

1，是在/etc/vimrc 进行设置，这种设置方法会作用与所有登录到Linux环境下的用户。不建议使用。

2，在用户登录的 ~ 目录下创建一个 .vimrc文件，在其中进行自己习惯的编程环境的设置，这样当别的用户使用实并不互相影响。


具体方法： 在文件中输入：

>set nu  // 这是设置显示行号

>set showmode    //设置在命令行界面最下面显示当前模式等。

>set ruler   // 在右下角显示光标所在的行数等信息

>set autoindent  // 设置每次单击Enter键后，光标移动到下一行时与上一行的起始字符对齐

>syntax on   // 即设置语法检测，当编辑C或者Shell脚本时，关键字会用特殊颜色显示

>highlight Comment ctermfg=green guifg=green     // 注释字体颜色太淡，调成绿色护眼

![linux_vim2.png][linux_vim2.png]

[ESC]
>：wq  // 保存 退出

[linux_vim0.png]:    {{site.url}}/assets/linux_vim0.png
[linux_vim1.png]:    {{site.url}}/assets/linux_vim1.png
[linux_vim2.png]:    {{site.url}}/assets/linux_vim2.png