---
layout: post
keyword: "sir-he,sir 何,sir何,sir-he blog,php,PHP Warning"
title:  "PHP Warning: Module 'modulename' already loaded in问题解决办法"
date:   2017-10-24
---

出现标题这样的错误大概是：
1. 模块加载了两次，所以 php -i\|grep Configure，看一下配置文件和配置include的目录，对于这些文件中是否有同名的module
2. 动态加载模块时，模块的目录下与php.ini中都有一个同名so
知道上述的问题就好办了，先看php配置文件和include目录下的文件，先整理内容。然后查看extension_dir，看看这个目录下的文件与include中的文件引用路径是否一致。