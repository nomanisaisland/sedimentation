# 线性结构（线性表结构）

线性结构就是数据排成像一条直线的结构

## 数组

### 概念

> 数组是一种线性表数据结构，它用一组连续的内存空间，来存储一组具有相同类型的数据

### 逻辑结构和物理结构

所谓的逻辑结构即我们可以用什么样的表达方式来描述数组，比如我们可以用（a1,a2,a3,...an）来描述数组中的每一个元素

所谓的物理结构即数组元素实际的存储形式，数组的物理存储空间就是一块连续的存储单元而已

#### 数组元素的访问

计算机给每一个内存单元都分配了一个地址，通过地址来访问其数据，因此要访问数组中的某个元素的时候，首先需要经过一个寻址公式计算要访问的元素在内存中的地址：

`a[i] = baseAdress + i * dataTypeSize`

其中dataTypeSize代表数组中元素类型的大小，比如int类型为四个字节

#### 数组下标为什么从0开始

从数组存储的内存模型上来看，“下标”最确切的定义应该是“偏移（offset）”。如果用array来表示数组的首地址，array[0] 就是偏移为0的位置，也就是首地址，array[k] 就表示偏移k个type_size的位置，所以计算array[k]的内存地址只需要用这个公式

`array[k]_address = base_address + k * type_size`

但如果从下标1开始，那么计算array[k]的内存地址会变成：

`array[k]_address = base_address + (k-1) * type_size`

对比两个公式，如果从1开始根据下标去访问元素，对于CPU来说就多了一次减法指令。

另一方面也是由于历史原因，C语言的设计者使用0开始作为数组的下标，后来的高级语言沿用了这一设计 

### 数组的特点

#### 高效的随机访问

可以快速地通过数组的首地址和寻址公式来快速地访问元素

#### 低效插入删除

为了保证数组的连续性，删除插入的时候需要移动很多元素，导致效率低下

##### 插入优化

如果数组的数据无序，则插入第k个位置时，直接将k位置原有的元素放到数据末尾后，将数据插入k位置

##### 删除优化

可以先记录已删除数据，每次删除操作并不是真的搬移数据，当数组没有更大空间了，再操作真正的删除（这也是JVM垃圾回收算法的操作）

### 数组的应用

#### ArrayList源码分析

#### 容器构建及添加元素

#### 获取元素





##  链表

### 概念

> 链表是一种物理存储单元上非连续、非顺序的存储结构，数据元素的逻辑顺序是通过链表中的指针链接次序实现的。链表由一系列节点（链表中的每一个元素称为节点）组成，节点可以在运行时动态生成。每个节点包含两个部分：一是存储数据元素的数据域，另一个是存储下一个节点地址的指针域

### 链表类型

#### 单链表

> 单链表是一种链式存取的[数据结构](https://baike.baidu.com/item/数据结构/1450)，用一组地址任意的[存储单元](https://baike.baidu.com/item/存储单元/8727749)存放线性表中的数据元素。链表中的数据是以结点来表示的，每个结点的构成：元素([数据元素](https://baike.baidu.com/item/数据元素/715313)的映象) +[ 指针](https://baike.baidu.com/item/ 指针/2878304)(指示后继元素[存储](https://baike.baidu.com/item/存储/1582924)位置)，元素就是存储数据的存储单元，指针就是连接每个结点的[地址](https://baike.baidu.com/item/地址/80420)数据。

特点：插入删除高效

插入和删除都只要讲指针指向最新的节点地址，再把原指针断掉就可以了

查询慢：

如果需要随机访问第k个元素的话，需要一个一个节点一次遍历，直到找到对应节点

#### 循环链表

> 是一种特殊的单链表，它跟单链表唯一的区别就在尾节点。单链表的尾节点指针指向空地址，表示这就是最后的节点了，而循环链表的尾节点指向链表的头节点。

#### 双向链表

> 单链表有两个方向，每个节点不止有一个后继指针next指向后面的节点，还有一个前驱指针prev指向前面的节点，和单链表对比，双向链表需要额外的两个空间来存储后继节点和前驱节点。所以如果存储同样多的数据，双向链表所占的空间要比单向链表多，但由于这个特性，双向链表支持双向遍历，使得双向链表更加的灵活

#### 双向循环列表

理解双向列表和循环列表的组合就可以了



数组和链表的对比：

1. 数组的优势是查询速度非常快，但是增删改查慢
2. 链表的优势是增删改查非常快，但是查询非常慢

## 栈

### 概念

> 先进后出，后进先出(last in first out)，从操作特点上来看，栈就是一种操作受限制的限制表，只允许在栈的一端进行数据的插入和删除，这两种操作的分别叫做入栈和出栈。当某个数据集合如果只涉及到在其一端进行数据的插入和删除的操作，并且满足先进后出，后进先出的特性时，我们应首选栈这种数据结构来进行数据存储

实际上，栈既可以用数组来实现，也可以用链表来实现。用数组实现的栈叫做顺序栈，用链表来实现的叫做链式栈

## 队列

### 概念

先进先出（first in first out）,队列和栈的操作受限，最基本的两个操作一个叫做入队列，将数据插入到队列尾部，另一个叫做出队列，从队列的头部取出一个数据

###　常见的队列

1. 顺序队列

   1. 队列可以使用数组来实现，用数组实现的队列叫做顺序队列

   ```java
   package com.iteima;
   
   public class ArrayQueue {
   //    定义队列结构
   //    使用数组来存储我们的元素
       private Object[] elements;
   //    定义队列的大小
       private int size;
   //    定义队列的初始容量
       private int DEFAULT_SIZE = 10;
   //    定义一个容器最大者
       private int MAX_ARRAY_SIZE = Integer.MAX_VALUE-8;  // 借鉴ArrayList源码
   //    定义队列头指针
       private int head;
   //    定义队列尾指针
       private int tail;
   
   //  定义一个默认初始化长度为10的队列
       public ArrayQueue() {
           elements = new Object[DEFAULT_SIZE];
   //        初始化首位指针
   //        this.head = 0;
   //        this.tail = 0;
           this.initPoint( 0,0 );
       }
       public ArrayQueue(int capcity) {
           if (capcity <= 0) {
               throw new RuntimeException("队列的初始容量有问题！");
           }
           elements = new Object[capcity];
           this.initPoint(0,0);
       }
       private void initPoint(int head, int tail) {
           this.head = head;
           this.tail = tail;
       }
   //    定义结构上的操作
   //    入队列(支持动态扩容)
       public boolean enqueue(Object element) {
   //    校验容量是否够用
           ensureSizeHelper();
           elements[tail++] = element;
           size++;
           return true;
       }
   //    出队列
       public Object dequeue() {
           if (head == tail) {
               return null;
           }
           Object object = elements[head++];
           size--;
           return object;
       }
   
   //    动态扩容机制
   //    1. 判断队列容量是否够用
       private void ensureSizeHelper() {
   //        尾指针已经越过队列的尾部
           if (tail == elements.length) {
               if (size < elements.length) {
                   if (head == 0) {
   //                    扩容操作
                   } else {
                       for (int i = head; i < tail; i++) {
                           elements[i-head] = elements[i];
                       }
                       initPoint(0,tail-head);
                   }
               }
           }
       }
   //    2. 扩容方法
       private void grow(int oldSize) {
           int newSize = oldSize + (oldSize >> 1); // 扩容1.5倍
           if (newSize - oldSize < 0) {
               newSize = DEFAULT_SIZE;
           }
           if (newSize - MAX_ARRAY_SIZE > 0) {
               newSize = capcityFinal(newSize);
           }
       }
       private int capcityFinal(int newSize) {
           return (newSize > MAX_ARRAY_SIZE) ? Integer.MAX_VALUE - 8 : newSize;
       }
   }
   ```

   

2. 链式队列

   1. 用链表实现的队列叫做链式队列

   ```java
   package com.iteima;
   /*
   * 1. 定义链表节点结构(单链表)
   * 2. 定义队列的结构
   * 3. 定义队列的操作
   *       入队列(链表的尾部添加一个元素)
   *       出队列(链表的头节点删除)
   * */
   public class LinkedListQueue {
   //    队列中元素个数
       private int size;
       private Node head;
       private Node tail;
   
       public LinkedListQueue() {
           this.head = null;
           this.tail = null;
       }
   
   //    入队列
       public boolean enqueue(Object element) {
           Node node = new Node(data, null);
           if (tail == null) {
               tail = node;
               head = node;
           } else {
               tail.next = node;
               tail = node;
           }
           size++;
           return true;
       }
   //    出队列
       public Object dequeue(){
           if (head == null) {
               return null;
           }
           Object data = head.data;
           head = head.next;
           if (head == null) {
               tail = null;
           }
           size--;
           return data;
       }
       /*
       * 链表的节点定义完毕
       * */
       static class Node {
           private Object data;
           private Node next;
           public Node(Object data,Node next) {
               this.data = data;
               this.next = next;
           }
       }
   }
   
   ```

   

3. 循环队列

4. 阻塞队列

5. 并发队列

......

> 队列应用场景：一般情况下，如果是对一些及时消息的处理，并且处理时间很短的情况下是不需要队列的，直接阻塞式的方法调用就可以了。但是如果在消息处理的时候特别费时间，如果这个时候有新的消息来了，就只能处于阻塞状态，造成用户等待。这个时候便需要引入队列了。当接收到消息后，先把消息放入队列中，然后再用新的线程进行处理，这个时候就不会有新的消息阻塞了，所以队列用来存放等待处理的元素集合，这种场景一般用于缓冲、并发访问，及时消息通信， 分布式消息队列等。

# 树形结构



# 图表结构

# 算法分析

```有关算法时间（计算次数）耗费分析，称之为时间复杂度分析.有关算法空间（占用内存）耗费分析，称之为空间复杂度分析```

## 算法的时间复杂度分析

### 事后分析估算法

程序写完后，用计时器计时，但是这样浪费时间，而且误差非常大，毕竟不同设备表现不同

### 事前分析估算法

编写前分析，一个高级语言编写的程序在计算机上运行所消耗的时间取决于以下因素：

1. 算法采用的策略和方案
2. 编译产生的代码质量
3. 问题的输入规模（所谓的问题输入规模就是输入量的多少）
4. 机器执行指令的速度



我们分析算法的运行时间，最重要的就是把核心操作的次数和输入规模关联起来



## 算法的空间复杂度分析

### 1. java中常见内存占用

| 数据类型 | 内存占用字节数 |
| :------: | :------------: |
|   byte   |       1        |
|  short   |       2        |
|   int    |       4        |
|   long   |       8        |
|  float   |       4        |
|  double  |       8        |
| boolean  |       1        |
|   char   |       2        |

### 2. 计算机访问内存都是一次一个字节（八个位）

### 3. 一个引用（机器地址）需要8个字节表示

例如： Date date = new Date()  date这个变量需要占用8个字节来表示



###  4. 创建一个对象，比如new Date(),除了Date对象内部存储的数据（例如年月日等信息）占用内存，该对象本身也有内存开销，每个对象的自身开销是16个字节，用来保存对象的头信息



### 5. 一般内存的使用，如果不够8个字节，都会被自动填充为8个字节

```java
public class A {
    public int a = 1;
}
// 通过new A() 创建一个对象内存占用如下：
// 1. 整型成员变量a占用4个字节
// 2. 对象本身占用16个字节
// 那么创建该对象总共需要20个字节，但由于不是以8位单位，会自动填充到24个字节
```

### 6. java中数组被先对为对象，他们一般都会因为记录长度而需要额外的内存，一个原始数据类型的数组一般需要24字节的头信息（16）个自己的对象开销，4字节用于保留长度以及4个填充字节，再加上保存值所需的内存。



```java
int n = arr.length // 申请4个字节
int [] tem = new int[n] // 申请n*4个字节，数组自身头信息开销24个字节  
// 以上代码空间复杂度为O(n)
int n = arr.length // 申请4个字节
// 以上代码空间复杂度为O(1)
```





# 复杂度分析

分析一个算法的运行时间，最重要的就是把核心操作的次数和输入的规模(n)关联起来,

```
2n+1 和 n+1 计算次数相差不多
n^2 和 2n+1  计算次数n^2远大于2n+1
随着输入规模的增大，与最高次项相乘的常数和相加得常数可以忽略

2n^2+3n+1 和 n^2 相比，计算次数相差不多
n^2 和 n^3  相比，n^3计算次数远大于n^2
最高次项指数大的，随着n的增长，结果也会变得增长得特别快

n^3  n^2  n  logn   k(常数) 相比  n^3 > n^2 > n > logn > k
算法函数中n最高次幂越小，算法效率越低
```

总结： 

1. 算法函数中得常数可以忽略
2. 算法函数中最高次幂得常数因子可以忽略
3. 算法函数中最高次幂越小，算法效率越高



## 函数渐近增长

> 给定两个函数f(n) 和 g(n), 如果存在一个整数N，使得对于所有的n>N，f(n)总是比g(n)大，那么我们说f(n)的增长渐近快于g(n)  

## 时间复杂度

### 大O记法

>  定义： 在进行算法分析时，语句总的执行次数T(n)是关于问题规模n的函数，进行分析T(n)随着n的变化情况并确定T(n)的量级。算法的时间复杂度，就是算法的时间度量，记作：T(n)=O(f(n))。它表示随着问题规模n的增大，算法执行时间的增长率和f(n)的增长率相同，称作算法的渐近时间复杂度，简称时间复杂度，其中f(n)是问题规模n的某个函数

``` 执行次数 = 执行时间 ```



大O阶的表示法可以有以下几个规则：

1. 用常数1取代运行时间中所有加法常数  4 =>  O(1)
2. 在修改后的运行次数中，只保留高阶项   n + 3 => O(n)
3. 如果最高阶项存在，且常数因子不为1，则去除与这个项相乘的常数   n^2 + 1 =>O(n^2)



### 常见的大O阶

### 1. 线性阶

一般含有非嵌套循环涉及线性阶，线性阶就是随着输入规模的扩大，对应计算次数呈直线增长，如：

```java
public static void main(String[] args) {
    int sum = 0;
    int n = 100;
    for (int i = 1;i< n;i++) {
        sum += i;
    }
    System.out.println("sum=" + sum);
}
```

上面这段代码，它的循环的时间复杂度为O(n),因为循环体中的代码需要执行n次

### 2.平方阶

一般嵌套循环属于这种时间复杂度

```java
public static void main(String[] args) {
    int sum = 0,n=100;
    for(int i = 1; i <= n ; i++ ){
        for(int j = 1; j <= n ; j++) {
            sum += i;
        }
    }
    System.out.println(sum);
}
```

时间复杂度为：O(n^2)

### 3. 立方阶

一般三层嵌套循环

O(n^3)

### 4. 对数阶

```java
int i = 1,n = 100;
while(i < n) {
    i = i * 2;
}
```

由于每次i * 2之后，就距离n更近了，假设有x个2相乘后大于n，则会退出循环。由于是2^x = n,得到x = log(2)n,所以这个循环的时间复杂度为O(logn)

对于对数阶，由于随着输入规模n的增大，不管底数多少，他们的增长趋势是一样的，所以我们会忽略底数

### 5.常数阶

一般不涉及循环操作的都是常数阶，因为他不会随着n的增长而增加操作次数

### 常见时间复杂度的总结

| 描述         | 增长的数量级 | 说明     | 举例           |
| ------------ | ------------ | -------- | -------------- |
| 常数级别     | 1            | 普通语句 | 将两个数相加   |
| 对数级别     | logN         | 二分策略 | 二分查找       |
| 线性级别     | N            | 循环     | 找出最大元素   |
| 线型对数级别 | NlogN        | 分治思想 | 归并排序       |
| 平方级别     | N^2          | 双层循环 | 检查所有元素对 |
| 立方级别     | N^3          | 三层循环 | 检查所有三元组 |
| 指数级别     | 2^ N         | 穷举查找 | 检查所有子集   |

复杂度排序：

O(1) < O(logn)  < O(n) < O(nlogn) < O(n^2) < O(n^3)



### 函数调用的时间复杂度分析

展开函数计算



### 最坏情况

假如有一个存储了n个随机数字的数组，请从中查找出指定的数字:

```java
public int search(int num) {
    int[] arr = {11,10,8,7345,234,23,12};
    for(int i = 0;i < arr.length; i++) {
        if(num === arr[i]) {
            return i;
        }
    }
    return -1;
}
```



最好的情况：

查找的第一个数字就是期望的数字，那么算法的时间复杂度为O(1)

最坏的情况：

查找的最后一个数字，才是期望的数字，那么算法的时间复杂度为O(n)

平均情况：

任何数字查找的平均成本是O(n/2)





# 排序算法

## 简单排序

### 1. 冒泡排序

排序原理： 

1. 比较相邻的元素，如果前一个元素比后一个元素大，就交换两个元素的位置
2. 对每一个相邻的元素做同样的工作，从开始第一对元素到结尾的最后一对元素。最终位置的元素就是最大值 

### 2. 选择排序

1. 每一次遍历的过程中，都假定第一个索引处的元素是最小值，和其他索引处的值依次进行比较，如果当前索引处的值大于其他某个索引出的值，则假定其他索引出的最小值，最后可以找到最小值所在的索引
2. 交换第一个索引处和最小值所在的索引处的值

选择排序的时间复杂度分析：

选择排序使用了双层for循环，其中外层循环完成了数据交换，内层循环完成了数据比较，所以我们分别统计交换和比较的次数：

```Java
// 数据比较： 
(N-1)+(N-2)+(N-3)+...+2+1= ((N-1)+ 1)*(N-1)/2=N^2/2-N/2;
//数据交换
N-1;
// 时间复杂度：
N^2/2-N/2 + (N-1) = N^2/2+N/2-1;
// 大o阶
O(N^2)
```

### 3.插入排序

排序原理：

1. 把所有的元素分为两组，已经排序和未排序，
2. 找到未排序的组中第一个元素，向已经排序的组中进行插入
3. 倒叙遍历已经排序的元素，依次和待插入的元素进行比较，直到找到一个元素小于或等于待插入元素，那么就把待插入元素放到这个位置，其他的元素向后移动一位

插入排序使用了双层循环，其中内部的循环体是真正完成排序的代码，只要分析内部循环体的执行次数

```java
// 最差情况
// 比较的次数为：
(N-1)+(N-2)+(N-3)+...+2+1= ((N-1)+ 1)*(N-1)/2=N^2/2-N/2;
//数据交换
(N-1)+(N-2)+(N-3)+...+2+1= ((N-1)+ 1)*(N-1)/2=N^2/2-N/2;
// 总的执行次数
(N^2/2-N/2) + (N^2/2-N/2) = N^2-N;
//大O阶
O(N^2)
```



## 高级排序

简单排序的时间复杂度都是O(N^2)

### 1. 希尔排序

> 希尔排序是插入排序的一种，又称“缩小增量排序”，是插入排序算法的一种高效的改进版本

排序原理：

1. 选定一个增量h，按照增量h作为数据分组的依据，对数组进行分组
2. 对分好组的每一组数据完成插入排序
3. 减小增量，最小减为1，重复第二步操作

![希尔排序](.\images\image-20210322224029838.png)

增长量h的确定：增长量的每一固定的规则，示例采用的是以下规则

```java
int h = 1;
while(h < 5) {
    h = 2h + 1;
}
// 循环结束后我们就可以确定h的最大值
// h的减少规则为：
h = h / 2 
```

### 2.归并排序



