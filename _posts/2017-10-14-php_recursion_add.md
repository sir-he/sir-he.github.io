---
layout: post
keyword: "sir-he,sir-he blog,php数组处理,php,php数组递加处理,何先生的博客"
title:  "php数组递加处理"
date:   2017-10-14 15:00:09
---

示例：

* 处理前：array ( 2 => 20, 3 => 40, 4 => 40, )
* 处理后：array ( 2 => 20, 3 => 60, 4 => 100, )

代码：

    <?php
        header("Content-type: text/html; charset=utf-8");
        $arr = [
            2 => 20,
            3 => 40,
            4 => 40,
        ];
        $len = count($arr);
        $keys = array_keys($arr);
        $values = array_values($arr);
        $newArr = [];
        $newArr[$keys[0]] = $values[0];
        for($i=0;$i<=$len;$i++){
            $tmp = $i+1;
            if(isset($values[$i]) && isset($values[$tmp])){
                $newArr[$keys[$tmp]] = $newArr[$keys[$i]] + $arr[$keys[$tmp]];
            }
        }
        echo '处理前：'.var_export($arr,true). "<br>" .'处理后：'.var_export($newArr,true);

<!--more-->

...