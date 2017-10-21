---
layout: post
keyword: "sir-he,sir-he blog,php,Iterator,迭代器,php迭代器Iterator作用"
excerpt: "什么是迭代器?迭代器的使用范围.php迭代器的实现.php迭代器的示例"
title:  "php迭代器Iterator作用"
date:   2017-10-21
tags:   [snorkel, lagos, portugal]
---

### 什么是迭代器?

迭代器有时又称光标（cursor）是程式设计的软件设计模式，可在容器物件（container，例如list或vector）上遍访的接口，设计人员无需关心容器物件的内容。

各种语言实作Iterator的方式皆不尽同，有些面向对象语言像Java, C#, Python, Delphi都已将Iterator的特性内建语言当中，完美的跟语言整合，我们称之隐式迭代器（implicit iterator），但像是C++语言本身就没有Iterator的特色，但STL仍利用template实作了功能强大的iterator。

### 迭代器的使用范围

1. 使用返回迭代器的包或库时（如PHP5中的SPL迭代器）
2. 无法在一次的调用获取容器的所有元素时
3. 要处理数量巨大的无素时（数据库中的表以GB计的数据）
4. ……

### php迭代器的实现

PHP5开始支持了接口， 并且内置了Iterator接口， 所以如果你定义了一个类，并实现了Iterator接口，那么你的这个类对象就是ZEND_ITER_OBJECT,否则就是ZEND_ITER_PLAIN_OBJECT.

对于ZEND_ITER_PLAIN_OBJECT的类，foreach会通过HASH_OF获取该对象的默认属性数组，然后对该数组进行foreach.

而对于ZEND_ITER_OBJECT的类对象，则会通过调用对象实现的Iterator接口相关函数来进行foreach。

说到迭代器这个东西，PHP内置的 迭代器还真多。迭代器到底来做什么的呢，其实就是用来遍历一个对象内部数据并且获得想要的结构。迭代器它可以控制foreach 语句的循环结构，通过适当的拓展可以获得指定情况下遍历的结果。就例如，PHP提供搜索，递归，聚集，XMl等各类型的迭代器。种类繁多，功能齐全，比如要处理个XML，用个simplexmliterator 就立马见效。

下面介绍一下最基础的几个迭代器的接口：

Traversable : 这个是最初始的接口，他提供了控制foreach 语句的内置功能。所谓内置，就是只由PHP核心器去控制，外部无法调用。也就是说这个接口是无法被外部应用所应用。

Iterator ： 这个接口继承了Traversable ，并且包含了控制foreach 的五个重要的函数 : rewind() , valid(), key(),current(),next() ，它实现了foreach每一步的动作。

iteratoraggregate : 这个接口以继承了Traversable, 它最大的功能是可以将实现Iterator的类移除在外，自身不用去实现那五个方法便可实现控制foreach的目的。

不同的迭代器有不同的接口，例如PHP SPL迭代器中包括Next()（移动到下一个元素）,corrent()（返回当前元素）,valid()（检查迭代结尾）,rewind()（从头重新开始）,key()（返回当前元素的索引）。当然你可以自己写适合自己用的迭代器，也可以用系统中的迭代器。

为什么要学习PHP的迭代器呢？我们不可以在foreach中去实现我们想要的处理呢。 其实，以上迭代器它本身的实现都是通过C拓展的，所以自己编写的遍历和PHP自身提供的迭代器是有性能的差异。第二个，因为遍历的是对象而不是数组，面不 来我们在遍历的时候遇到不少麻烦，即使我们解决了，也不能确保我们应用到的算法是最好的，而迭代器就是集成了最优化的算法。所以，以后开发中尽量使用迭代 器去做想做的事情吧。利用PHP的迭代器可以利用面向对象实现常见的数据结构，例如列表，堆栈，队列与图。

### php迭代器的示例

    <?php
    class MyIterator implements Iterator{
        protected $position;
        protected $arr;
        public function __construct($array){
            $this->arr = $array;
            $this->postion = 0;
        }
        public function rewind(){
            var_dump(__METHOD__);
            $this->position = 0;
        }
        public function valid(){
            var_dump(__METHOD__);
            return isset($this->arr[$this->position]);
        }
        public function key(){
            var_dump(__METHOD__);
            return $this->position;
        }
        public function current(){
            var_dump(__METHOD__);
            return $this->arr[$this->position];
        }
        public function next(){
            var_dump(__METHOD__);
            return ++$this->position;
        }
    }
    // 例子
    $array = array(1,2,3,3,4);
    $it = new MyIterator($array);
    foreach($it as $key=>$value){
        echo $key.':'.$value.'<br/>';  
    }

使用iteratoraggregate :

    class MyIteratorAggregate implements IteratorAggregate{
        protected $arr;
        public function __construct($array){
            $this->arr = $array;
        }
        public function getIterator(){
            return new MyIterator($this->arr);
        }
    }
    //例子：
    $array = array(1,2,3,3,4);
    $it = new MyIteratorAggregate($array);
    foreach($it as $key=>$value){
        echo $key.':'.$value.'<br/>';
    }
