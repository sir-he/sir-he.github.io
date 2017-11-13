---
layout: post
keyword: "sir-he,sir 何,sir-he blog,何先生的博客,php,post提交,跳转"
title:  "php post提交跳转"
date:   2017-11-13
---

有些时候 可能需要一些post提交跳转的操作 比如一些支付等 下面是一个post提交跳转的例子

    <?php
    header("Content-type: text/html; charset=utf-8");
    $arr = array(
      'ss' => 11,
      's1' => 11,
      's2' => 11,
    );
    $sHtml = "<form id='apisubmit' name='apisubmit' action='test2.php' method='post'>";
    while (list ($key, $val) = each ($arr)) {
      $sHtml.= "<input type='hidden' name='".$key."' value='".$val."'/>";
    }
    $sHtml = $sHtml."<input type='submit' value='".$button_name."' style='display:none'></form> 正在跳转 ……";
    $sHtml = $sHtml."<script>document.forms['apisubmit'].submit();</script>";
    echo $sHtml;