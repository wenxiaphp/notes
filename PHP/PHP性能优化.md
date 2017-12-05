## PHP 的性能问题的解决方向

1. PHP语言级的性能优化
2. PHP周边问题的性能优化
3. PHP语言自身分析、优化
【注意】困难度：从容易到困难

## 压力测试工具简介

### Apache Benchmark（简称：ab）

简介：ab是由apache提供的压力测试软件，安装apache服务器是会自带压力测试软件
具体安装：自己安装或者参考网上的资料安装

如何使用：例如：通过ab软件向http://www.baidu.com以100个并发发起1000个请求来实现一个压力测试

./ab -n1000 -c100 http://www.baidu.com/
> -n：表示的是请求数，通过ab的软件，向目标地址发起1000个请求数
> -c：表示并发数，我们以100个并发，项目地址发送请求
> http://www.baidu.com/： 表示目标地址

## ab软件的使用

可以输入 ab -h （ab -help）
常用的命令：
ab -n：表示要发送多少请求
ab -c：表示并发数

通过ab软件向http://www.baidu.com以100个并发发起1000个请求来实现一个压力测试，返回结果解析
./ab -n100 -c10 http://www.baidu.com/

【解析】
- Request per second： 101.66    表示每秒可以处理101个请求（越大越好）
- Time per request：9.838[ms]   表示处理一个请求需要的时间（越小越好）

## PHP语言级性能优化

- 优化点：
少写代码，多用PHP自身的能力

- 性能问题：
自卸代码冗余较多，可读性不佳，并且性能低

- 为什么性能低：
PHP代码需要编译解析为底层语言，这一过程每次请求都谁处理一遍，开销大

- 好的方法：
多使用PHP内置变量、常量、函数

### 测试两种方式的区别

提前准备两份代码：
./bad.php
```php
<?php
    //准备两个数组，数组内容随机
    $array_1 = array();
    $array_2 = array();
    for($i=0 ; $i<rand(1000,2000);$i++){
        $array_1[] = rand();
    }
    for($i = 0 ; $i < rand(1000,2000) ; $i ++ ){
        $array_2[] = rand();
    }
    //将两个数组合并为一个数组
    //重复的元素仅保存一次
    $array_merged = array();

    /*
    思路：先将数组1逐个加入到目标数组中，然后遍历数组2，对数组2内每个元素，看看是否在数组1中存在；如果存在，忽略该元素；如果不存在，将该元素添加进去
    */
    foreach ($array_1 as $value) {
        $array_merged[] = $value;
    }
    foreach ($array_2 as $value) {
        if(!in_array($value,$array_merged)){
            $array_merged[] = $value;
        }
    }
    var_dump($array_1,$array_2,$array_merged);
 ?>
```
./good.php
```php
<?php
    $array_1 = $array_2 = range(1000,2000);
    shuffle($array_1); //将数组打乱
    shuffle($array_2);
    $array_merged = array_merge($array_1,$array_2); //合并两个数组
    var_dump($array_1,$array_2,$array_merged);
 ?>
```

先找到访问该php的文件路径
结果比较：
1、bad.php：
ab -n100 -c10 http://127.0.0.1/bad.php
【结果】
- Request per second： 28.56
- Time per request：35.016[ms]

2、good.php：
ab -n100 -c10 http://127.0.0.1/good.php
【结果】
- Request per second： 392.50
- Time per request：2.548[ms]

### PHP代码运行流程

php代码运行流程：
- zend引擎逐行扫描*.php文件转码解析成自己能识别的格式，再解析成opcodes（最终执行的机器码），执行，输出。
- PHP缓存多使用opcode缓存,可以减少编译解析，提高效率加快速度。
- php内置函数会节省扫描转码的时间，生成的opcode体积也会小，执行也快，所以内置函数是比自己写的代码运行的速度要快的。

### PHP 内置函数的性能优劣

- 情况描述：
PHP内置函数之间依然存在快慢差异
- 好的建议：
多去了解PHP内置函数的时间复杂度

### PHP内置函数比较

举例：通过使用isset() 与 array_key_exists() 方法间的性能差异

```php
<?php
    //获取开始的时间戳，精确到微秒
    $start = current_time();
    $i = 0 ;
    $arr = range(1,200000);
    while ($a < 200000) {
        ++ $i;
        //isset($arr[$i]); // 循环200000次，平均50ms
        array_key_exists($i,$arr); //循环200000次，平均85ms
    }
    //获取结束的时间戳，精确到微秒
    $end = current_time();
    ehco "lost Time：".number_format($end-$start,3)*1000;
    echo '\n';
    //microtime()获取精确到微秒的时间戳
    function current_time(){
        list($usec,$sec) = explode(" ",microtime());
        return ((float)$usec + (float)$sec);
    }
 ?>
```
