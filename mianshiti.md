### 两行代码的PHP面试题
请问，输出什么，为什么？
~~~
<?php

$str='php';
$str['name']=array('dogstar');

var_dump($str);
~~~





这道面试题下面说，如果能答对，至少说明两点
* 你是一个细心的人
* 对PHP语言的理解非常到位

网友的答案很多，回答最多的答案就是，输出一个数组，即：array('dogstar')。
因为在他们认为，把字符串当做数组使用，会把变量转换一个数组类型，所以得出这个结果。





~~~
<?php

$str='php';				//把字符串赋值给了变量$str
$str['name']=array('dogstar');
var_dump($str);
~~~
别急看代码，首先看代码之前我们回顾一下基础知识！



php的基本数据类型都有哪些？(官方链接：http://php.net/manual/zh/language.types.php)
<img src="/home/tt/php数据类型.png" style="zoom: 67%;" />




先看一个简单的代码
~~~
$arr=array();

$arr[0] = 'A';
$arr['x'] = 'B';
$arr[1] = 'C';
$arr['y']= 'D';
$arr[] = 'E';			//没有下标
~~~
问：最后E字母对应的数组下标是什么？





PHP数组的下标类型，PHP官方文档有记载，http://php.net/manual/zh/language.types.array.php
<img src="/home/tt/图片/数组.png" style="zoom: 67%;" />
读取关键信息`// 键（key）可以是一个整数 integer 或字符串 string`
就是说，PHP数组的下标由两种类型，一种是整数，一种是字符串





输出一下下面代码

~~~
$a = 'PHP';

echo $a[0],"<br>";
echo $a[1],"<br>";
echo $a[5],"<br>";
~~~
php中的字符串可以当做一个数组的形式








~~~
<?php

$str['name'] = array('dogstar');
~~~
$str不是一个字符串，是一个数组。
* PHP字符串可以通过下标操作，但是有效的是0、1、2这种数字
* PHP下标由两种类型，可以是整数或者是字符串






看一下字符串转整数的规则
~~~
<?php

echo intval('123'),"<br>";
echo intval('asd'),"<br>";
echo intval('123asd'),"<br>";
echo intval('asd123'),"<br>";
echo intval('1as2d3'),"<br>";
~~~

php转换整型的规则，（官方链接http://php.net/manual/zh/language.types.string.php#language.types.string.conversion）
![](/home/tt/图片/php数据转换规则.png)

简单来说，从第一个开始，一直连续的有效部分都会转换成整数







~~~
<?php
$str = 'php';
$str['name']=array('dogstar');
var_dump($str);

转换整数，即
<?php
intval('name');
~~~
结果很容易得出，字符串"name"会转换成0





现在看一下整体的题
~~~
<?php
$str = 'php';
$str['name']=array('dogstar');
var_dump($str);

变成了
<?php
$str = 'php';
$str['0']=array('dogstar');
var_dump($str);
~~~





下面进行php的数组转换成字符串

~~~
<?php
echo strval(array('dogstar'));			//结果为？
~~~

随意题目简化成了
~~~
<?php
// $str['name'] = array('dogstar');
// $str[0] = array('dogstar');
$str[0] = 'Array'; 
var_dump($str);
~~~
所以答案为：