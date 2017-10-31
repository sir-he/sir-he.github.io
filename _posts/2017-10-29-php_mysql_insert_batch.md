---
layout: post
keyword: "sir-he,sir 何,sir-he blog,php,mysql,php批量插入数据到mysql,数组写入数据库"
title:  "php批量插入数据到mysql"
date:   2017-10-29
---

    <?php
        $a = array (
            '西瓜' => 'xigua',
            '橘子' => 'juzi'
        );  
           
        $value_str = '';
        foreach ( $a as $key => $val ) {
            $value_str [] = "'" . $key . "','" . $val . "'";
        }
        $s="insert into table_name (`name`,`pinyin`) values ("  
                 .implode ( "),(", $value_str ) . ")";
        echo $s;

insert into table_name (`name`,`pinyin`) values ('西瓜','xigua'),('橘子','juzi')