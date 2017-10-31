---
layout: post
keyword: "sir-he,sir 何,sir-he blog,何先生的博客,php,mysql,pdo,php pdo curd"
title:  "php使用pdo操作mysql增删改查"
date:   2017-10-30
---

    <?php
    header("content-type:text/html;charset=utf-8");  
    $dsn="mysql:dbname=test;host=localhost";  
    $db_user='root';  
    $db_pass='admin';  
    try{  
        $pdo=new PDO($dsn,$db_user,$db_pass);  
    }catch(PDOException $e){  
        echo '数据库连接失败'.$e->getMessage();  
    }  
    //新增  
    $sql="insert into buyer (username,password,email) values ('ff','123456','admin@admin.com')";  
    $res=$pdo->exec($sql);  
    echo '影响行数：'.$res;  
<!--more-->
    //修改  
    $sql="update buyer set username='ff123' where id>3";  
    $res=$pdo->exec($sql);  
    echo '影响行数：'.$res;  
    //查询  
    $sql="select * from buyer";  
    $res=$pdo->query($sql);
    $arr=$res->fetch(); //查询一条
    $arr=$res->fetchAll();  //查询全部
    foreach($res as $row){  
        echo $row['username'].'<br/>';  
    }  
    //删除  
    $sql="delete from buyer where id>5";  
    $res=$pdo->exec($sql);  
    echo '影响行数：'.$res; 

* 更多请查看[php官方网站](http://php.net/manual/en/book.pdo.php)