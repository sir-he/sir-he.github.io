---
layout: post
keyword: "sir-he,sir 何,sir-he blog,何先生的博客,免费接口"
title:  "程序员福利：各大平台免费接口，非常实用"
date:   2017-11-17
---

* 手机信息查询接口

淘宝网接口：

>http://tcc.taobao.com/cc/json/mobile_tel_segment.htm?tel=手机号

* 谷歌接口

FeedXml转json接口：

>http://ajax.googleapis.com/ajax/services/feed/load?q=Feed地址&v=1.0

备选参数:callback：&callback=foo就会在json外面嵌套foo({})方便做jsonp使用。
备选参数:n：返回多少条记录。


* 物流接口

快递接口：

>http://www.kuaidi100.com/query?type=快递公司代号&postid=快递单号

ps:快递公司编码:申通=”shentong” EMS=”ems” 顺丰=”shunfeng” 圆通=”yuantong” 中通=”zhongtong” 韵达=”yunda” 天天=”tiantian” 汇通=”huitongkuaidi” 全峰=”quanfengkuaidi” 德邦=”debangwuliu” 宅急送=”zhaijisong”

* 电商接口
<!--more-->

京东获取单个商品价格接口：

>http://p.3.cn/prices/mgets?skuIds=J_商品ID&type=1

ps:商品ID这么获取:http://item.jd.com/5025518.html

* 地图接口

阿里云根据地区名获取经纬度接口：

>http://gc.ditu.aliyun.com/geocoding?a=苏州市

参数解释: 纬度,经度type 001 (100代表道路，010代表POI，001代表门址，111可以同时显示前三项)

阿里云根据经纬度获取地区名接口：

>http://gc.ditu.aliyun.com/regeocoding?l=39.938133,116.395739&type=001

* IP接口

新浪接口（ip值为空的时候 获取本地的）：

>http://int.dpool.sina.com.cn/iplookup/iplookup.php?format=json&ip=218.4.255.255

淘宝接口：

>http://ip.taobao.com/service/getIpInfo.php?ip=63.223.108.42
