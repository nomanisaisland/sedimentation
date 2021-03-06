# PHP

## 什么是php（PHP Hypertext Preprosessor）

> php 定义：一种服务器端的html脚本/编程语言，是一种简单的，面向对象的、解释型的、健壮的、安全的、性能非常之高的、独立于架构的、可移植性的、动态脚本语言，是一种管饭用于Open Source（开放源码）的尤其适合web开发并可以嵌入html的多用途脚本语言，他的语法接近于c,java,perl,而且容易学习。该语言让web开发人员快速的书写动态生成的网页

 ## 服务器

服务器（server），也称伺服器，是提供计算服务的设备，由于服务器需要响应服务请求，并进行处理，因此一般来说服务器应具备承担服务并且保障服务的能力

服务器：能够提供服务的机器，取决于机器上所安装的软件（服务软件）

在网络环境下，根据服务器提供的服务类型不停，分为文件服务器和数据库服务器，应用程序服务器，web服务器等

## IP

IP：internet Protocol,网络之间的互联协议，网络之间互联的协议也就是为了计算机网络相互连接进行通信而设计的协议，在因特网中，他是能是连接到网上的所有计算机网络实现互相通信的一套规则，规定了计算机在因特网上进行通信时应遵守的规则，任何厂家生产的计算机系统，只要遵守ip协议就可以与因特网互连互通，IP地址具有唯一性

## 域名（Domain Name）

域名是由一串用电分隔的名字组成（www.baidu.com）的Internet上某一台计算机或计算机组的名称，用于在数据传输时标志计算机的电子方位（有时也指地理位置，地理上的域名，指代有行政自主权的一个地方区域），域名是一个ip地址上由“面具”。一个域名的目的是便于记忆和沟通的一组服务器的地址

特殊ip： 127.0.0.1 代表本机

特殊域名：localhost

## DNS

DNS（Domain Name System，域名系统），因特网上作为域名和IP地址相互映射的一个分布式数据库，能够使用户更方便的访问互联网，而不用去记住能过够被机器直接读取的ip数串，通过主机名，最终得到该主机名对应的Ip地址的过程叫做域名解析（或主机名解析）

## 端口

端口（Port），可以认为是设备与外界铜须交流的出口，端口可分为虚拟端口和物理端口，其中虚拟端口只计算机内部或交换机路由器内的端口，不可见，例如计算机中的80端口、21端口等，计算机背版的RJ45网口，交换机路由器集线器等RJ45端口

## WEB程序的访问流程

web分为两种：静态网站和动态网站

动态网站的访问流程：

浏览器发起访问==》DNS解析（找ip）==》 服务器电脑（通过端口识别对应的）==》服务软件

静态访问：

![](F:\学习笔记\image\Screenshot_20200531-174819.jpg)



动态网站访问流程：

![](F:\学习笔记\image\Screenshot_20200531-175354.jpg)

## [Apache安装](https://www.jianshu.com/p/3fd8ac3b937c)

下载服务

```shell
httpd.exe -k install -n apache
```





![image-20200531182414812](F:\学习笔记\image\image-20200531182414812.png)

以下命令需要配置环境变量

### 查看使用模块： httpd -M

static 表示静态加载： Apache启动就加载好了，可以直接使用

shared 表示动态加载：在使用到的时候才会加载

### 验证配置文件是否有效： httpd -t

## 配置默认站点

1. 让Apache确定服务器上访问的位置：网站文件夹所在的位置

   config 下的 Define SRVROOT

2. 方便用户使用名字访问对应的网站：给文件夹对应的去一个名字

   config 下的 ServerName

   1.  端口可以单独实现

      config 下的listen

3. 凡是涉及到Apache配置文件的修改，那么需要重启Apache才能生效

4. 实现DNS域名解析：通常默认站点都是本地DNS：hosts文件

   ​	C:\Windows\System32\drivers\etc\hosts

## [下载PHP](https://windows.php.net/download)

解压后把文件放在Apache同文件下

## 配置Apache加载PHP模块

1. Apache加载PHP模块：在Apache的著配置文件中加载对应的PHP提供的模块

LoadModule php7_module（7代表当前PHP版本） PHP 所提供的模块链接所在路径

在httpd.config 文件的LoadModule模块下加入一个

```
LoadModule php7_module 'D:\php7\php7apache2_4.dll'
```

这样就配置号PHP模块了

``` shell
F:\server\httpd-2.4.43-o111g-x86-vc15\Apache24\bin httpd.exe -t  #来验证是否加载成功
```

# PHP基础

## PHP语法标记

1. ASP 标记： <% php代码 %>
2. 短标记： <?php代码 ?>
3. 脚本标记: <script language="php">php代码</script>
4. 标准标记：<?php php代码 ?>

## 注释

// 单行注释

\# 与//一样是单行注释

/**/ 多行注释，块注释

## PHP语句分隔符

php通过分号判断行的结束

## PHP建议不使用?>闭合

闭合标签后面如果有空格或者换行的话会解析为html

```php
<?php
	.....;
```

## 变量

使用$定义

使用unset($a) 删除变量

### 预定义变量

预定义变量：提前定义的变量，系统定义的变量，存储许多需要用到的数据(预定义变量都是数组)

```php
$_GET;  // 获取所有表单以get方式提交的数据
$_POST;  // POST提交的数据都会保存在次
$_REQUEST;  // GET 和POST提交的数据都会保存
$GLOBALS; // PHP中所有的全局变量
$_SERVER; // 服务器信息
$_SESSION; // session会话数据
$_COOKIE; // cookie会话数据
$_ENV; // 环境信息
$_FILES; // 用户上传的文件信息
```

### 可变变量

可变变量：如果一个变量保存的值刚好是另外一个变量的名字，那么可以直接通过访问一个变量得到另外一个变量的值：在变量前面再多加一个$符号

```php
$a = 'b';
$b = 'bb';
$$a -> bb
```

### 变量传值

两种方式： 值传递，引用传递

## 变量命名规则

1. 以$为开头
2. 名字由字母、数字和下划线构成，数字不能为开头

## 常量

常量的定义由两种方式: 函数式和关键字

```php
define('name','张三');
const name = '张三';
```

命名规则：

1. 常量不适用$符号
2. 常量的名字由字母、数字和下划线组成
3. 常量的名字通常是以大写字母为主
4. 常量可以用一些特殊字母，该方式只能使用define定义: define('-_-','a')

#### define和const定义的区别：



#### 特殊名字常量的访问方式

constant('-_-')

### 系统常量

系统定义的，用户直接用：

```php
PHP_VERSION; // php版本号
PHP_INT_SIZE; // 整型大小
PHP_INT_SIZE; // 整型能表示的最大值（PHP中整型是允许出现负数的，带符号）
```

在php中还有一些特殊的常量，他们有双下划线开始+常量名+双下划线结束，这种常量称之为系统魔术常量：魔术常量的值通常会跟着环境变化，但是用户改变不了

```php
__DIR__; // 当前被执行的脚本所在电脑的绝对路径
__FILE__; //当前被执行的脚本所在的电脑的绝对路径（带自己文件的名字）
__LINE__; // 当前所属的行数
__NAMESPACE__; // 当前所属的命名空间
__CLASS__; // 当前所属的类
__METHOD__: // 当前所属的方法
```

## 数据类型

数据类型：data type，在php中指的是存储的数据本身的类型，而不是变量的类型，php是一种弱类型语言，变量本身没有数据类型

#### 三大类八小类

##### 简单（基本）数据类型：4小类

整型：int/integer,系统分配4个字节存储，表示整数类型（有前提）,最大32位42亿多，可以以二进制（ob开头），八进制，十进制，十六进制（0x开头）定义

浮点型：float/double,系统分配8个字节存储，表示小数或者整型存不下的整数(不保证精度，精度范围大概在15个有效数字左右),

字符串类型： string, 系统根据时机长度分配

布尔类型：bool/boolean,表示布尔类型，Empty()判断值是否为空，如果为空返回true，否则false，isset()判断数据存储的变量本身是否位空，存在变量返回true，不存在返回false

##### 特殊类型：2小类

资源类型：resource,存放资源数据（php外部数据，如数据库、文件）

空类型：NULL，只有一个值就是NULL



浮点数为什么存的比整数多

00000000 00000000 00000000 00000000 -> 11111111 11111111 11111111 11111111

整数每个数字都是有效数字，浮点数从第二个数到第八个数计算的结果是10的指数

### 类型转换

自动转换：系统根据需求自己判断，自己转换

强制转换

```php
$a = '123';
(int) a;
(integer) a;
```

### 类型判断

```php
is_xxx(变量名);
is_int($a);
var_dump($a); // 查询类型
Gettype(变量名); // 得到该类型对应的字符串
Settype(变量名,类型) //设置变量类型  和自动转换的不同是会改变数据本身类型
```

### 进制转换

十进制转二进制： 方法1：除2取余，不管结果如何，需补足32位，前面补余   方法2：从二进制右侧开始，按照对应的指数次位置补1，没有的补0

二进制转十进制：从右侧开始当前位置值*2的当前位置次幂（从0开始）

php中自带的函数转换方式：

Decbin(): 十进制转二进制

Decoct(): 十进制转八进制

Dechex(): 十进制转十六进制

......



## 运算符

### 赋值运算符： 

=

### 算术运算符

\+,-,*,/,%

### 比较运算符

```php
> >= < <= == != === !==
```

### 逻辑运算符

```
&&逻辑与  ||逻辑或  !逻辑非
```

### 连接运算符

```
.  将两个字符串连接到一起
.= 复合运算
$a .= $b -> $a = $a . $b
```

错误抑制符

```
@ 
@($a/$b) 有错不会报
错误抑制符常在生产环境会用到
```

### 三目运算符

```
表达式1 ? 表达式2 : 表达式
```

### 自操作运算符

```
++  -- += -= /= %=
```

### 计算机码

计算机在时机存储的时候，采用的编码规则（二进制规则）

计算机码： 原码、反码和补码，数值本身最左边一位是用来充当符号位：整数位0，负数位1

原码：数据本身从十进制转换成二进制得到的结果

​	正数：左边符号位为0；（整数的原码、反码和补码就是本身）

​	负数：左边符号位为1

反码：针对负数，符号位不变，其他位取反

补码：针对负数，反码+1

系统中存在两个0：+0和-0

+0：00000000；

-0： 10000000；原码

取反：11111111

补码：00000000

```
5原码：00000101
-5原码:10000101
取反：11111010  // 反码：符号位不变，其他位取反
求补：11111011  // 补码：反码+1
```

### 位运算

取出计算机中最小的单位进行运算

```
&  按位与
!  按位或
~  按位非
^  按位异或
<< 按位左移
>> 按位右移
```

注意：

1. 系统进行任何位运算符的时候都是使用的补码
2. 运算结束之后都必须转换为原码才是最终要显示的数据

### 运算符优先级



## 安装composer

## 安装laravel

```shell
composer create-project --prefer-dist laravel/laravel blog "5.5.*"
```

