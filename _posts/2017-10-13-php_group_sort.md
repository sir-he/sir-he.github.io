---
layout: post
keyword: "sir-he,sir-he blog,array_multisort,php数组排序,php分组,php数组分组排序"
excerpt: "php数组利用array_multisort函数分组排序"
title:  "php数组分组排序"
date:   2017-10-13 23:29:06
tags:   [snorkel, lagos, portugal]
---

过程很简单,分为两步
1. 对数组进行分组
2. 新的数组根据某字段排序

举个例子(先看演示,后附有代码)：

***排序前数组：***


    [0] => Array
        (
            [id] => 1
            [routeFlag] => 1
            [bankAbbr] => ABC
            [prilvl] => 99
        )
    [1] => Array
        (
            [id] => 2
            [routeFlag] => 1
            [bankAbbr] => BOB
            [prilvl] => 101
        )
    [2] => Array
        (
            [id] => 2
            [routeFlag] => 0
            [bankAbbr] => ABC
            [prilvl] => 100
        )
    [3] => Array
        (
            [id] => 2
            [routeFlag] => 0
            [bankAbbr] => BOB
            [prilvl] => 10
        )
    [4] => Array
        (
            [id] => 2
            [routeFlag] => 1
            [bankAbbr] => PABC
            [prilvl] => 10
        )

***根据 key=>bankAbbr 分组后数组：***

    [ABC] => Array
        (
            [0] => Array
                (
                    [id] => 1
                    [routeFlag] => 1
                    [bankAbbr] => ABC
                    [prilvl] => 99
                )
            [1] => Array
                (
                    [id] => 2
                    [routeFlag] => 0
                    [bankAbbr] => ABC
                    [prilvl] => 100
                )
        )
    [BOB] => Array
        (
            [0] => Array
                (
                    [id] => 2
                    [routeFlag] => 1
                    [bankAbbr] => BOB
                    [prilvl] => 101
                )
            [1] => Array
                (
                    [id] => 2
                    [routeFlag] => 0
                    [bankAbbr] => BOB
                    [prilvl] => 10
                )
        )
    [PABC] => Array
        (
            [0] => Array
                (
                    [id] => 2
                    [routeFlag] => 1
                    [bankAbbr] => PABC
                    [prilvl] => 10
                )
        )

***根据 key=>prilvl 倒序排序后数组：***

    [ABC] => Array
        (
            [0] => Array
                (
                    [id] => 2
                    [routeFlag] => 0
                    [bankAbbr] => ABC
                    [prilvl] => 100
                )
            [1] => Array
                (
                    [id] => 1
                    [routeFlag] => 1
                    [bankAbbr] => ABC
                    [prilvl] => 99
                )
        )
    [BOB] => Array
        (
            [0] => Array
                (
                    [id] => 2
                    [routeFlag] => 1
                    [bankAbbr] => BOB
                    [prilvl] => 101
                )
            [1] => Array
                (
                    [id] => 2
                    [routeFlag] => 0
                    [bankAbbr] => BOB
                    [prilvl] => 10
                )
        )
    [PABC] => Array
        (
            [0] => Array
                (
                    [id] => 2
                    [routeFlag] => 1
                    [bankAbbr] => PABC
                    [prilvl] => 10
                )
        )

### 以下是代码部分

------------------
    
    <?php
    header("Content-Type: text/html; charset=utf-8");
    $str = '[{"id":"1","routeFlag":"1","bankAbbr":"ABC","prilvl":"99"},{"id":"2","routeFlag":"1","bankAbbr":"BOB","prilvl":"101"},{"id":"2","routeFlag":"0","bankAbbr":"ABC","prilvl":"100"},{"id":"2","routeFlag":"0","bankAbbr":"BOB","prilvl":"10"},{"id":"2","routeFlag":"1","bankAbbr":"PABC","prilvl":"10"}]';
    $list = json_decode($str, true);
    // echo "<pre>";
    // print_r($list);die;
    $arr = array();
    $newArr = array();
    foreach($list as $key => $val){ //分组
        $newArr[$val['bankAbbr']][] = $val;
    }
    foreach($newArr as $key => $val){  //排序
        $arr[$key] = multi_array_sort($val, 'prilvl');
    }

    $ar = array();
    foreach($arr as $key => $val){  //取值
        $str = '';
        foreach($val as $k => $v){
            $str = $str.$v['routeFlag'].',';
        }
        $str = substr($str,0,strlen($str)-1);
        $ar[$key] = $str;
    }
    echo "排序前数组：<pre>";
    print_r($list);
    echo "</pre>";

    echo "根据key=>bankAbbr分组后数组：<pre>";
    print_r($newArr);
    echo "</pre>";

    echo "根据key=>prilvl倒序排序后数组：<pre>";
    print_r($arr);
    echo "</pre>";
    
    //排序方法
    function multi_array_sort($multi_array,$sort_key,$sort=SORT_DESC){
        if(is_array($multi_array)){
            foreach ($multi_array as $row_array){
                if(is_array($row_array)){
                    $key_array[] = $row_array[$sort_key];
                }else{
                    return false;
                }
            }
        }else{
            return false;
        }
        array_multisort($key_array,$sort,$multi_array);
        return $multi_array;
    }
