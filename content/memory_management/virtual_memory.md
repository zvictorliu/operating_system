---
title: 虚拟内存
---

先知道一下*局部性原理*

虚拟存储器的思想是：

- 作业只先把当前需要的那部分程序和数据装入内存，当运行到没有的时，再次装入
- 将暂时不用的部分换出去，需要时再换进来
- 内存能装入的进程变多，逻辑上空间变大

为实现虚拟存储器，有三种方式：

- 请求分页（最主要）、请求分段、请求段页

和前面的基本xxx相比，这属于”请求“，这个是特点

只学请求分页

## 1 请求分页管理方式

能实现调入所需页面、置换暂时不需要的页面

需要的硬件支持：

- 页表
- 缺页中断：想来真tm合理
- 地址变换

### 1.1 页表

多增加了几个字段的原因：

- 为实现请求，需要知道页面当前在不在内存中，同时还需要知道在外存中的位置
  - 有点忘了基本分页为什么不需要外存地址了，，，，，
- 内存不够需要置换时，需要有依据决定哪些是可以换出去的，此外，如果页面没有被修改过的话就不需要再将其写一遍到外存，因此还有一个记录是否被修改的

所以，多出来了四个字段：

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230515200636970.png" alt="image-20230515200636970" style="zoom:70%;" />

### 1.2 缺页中断

页面不在内存，就产生中断，为的是请求操作系统来把需要的页调入内存

在等待操作系统完成时，将该进程阻塞，完成后再唤醒放入就绪队列

如果没有空闲块就需要进行淘汰换出了

这种中断的特点是：

- 是内部异常，在指令执行期间产生和处理

  - 类似于”找不到文件“的异常

  <img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230515201414793.png" alt="image-20230515201414793" style="zoom:60%;" />

- 它是可以在一条指令执行期间产生中断的，是一种内部异常

- 一条指令可能有多次缺页中断

### 1.3 地址变换

程序请求访问一页，需要经过地址变换得到在内存中的物理地址，这个过程其实经历了许许多多if else的判断

基本分页方式都认为页就在内存当中，所以不会有请求调入和页面置换这两个步骤

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230515203822605.png" alt="image-20230515203822605" style="zoom:80%;" />

会先检索快表（这个忘了）

## 2 页面置换算法

很简单就是如何选择哪个该换出去的算法，有四种

- 最佳置换OPT
- 先进先出FIFO
- 最近最久未使用LRU
- 时钟

### 2.1 OPT

### 2.2 FIFO

### 2.3 LRU

### 2.4 Clock

简单型和改进型

## 3 页面分配策略

页框是内存的”页“，这节研究给特定的进程分配多少页框，很类似于内存的划分了

- 太少了，虽然能放的进程多了，但每个进程缺页的概率很高（即使有局部性原理）

- 太多了，由于局部性原理可能根本不需要很多，缺页率不会降低太多

> 这部分感觉不是重点，但是也可能考，，，所以，，唉
>
> 现在先粗略看一遍就行了

### 3.1 分配策略

对于请求分配的系统来说，根据内存分配的策略和置换的策略，有三种：

- 固定分配+局部置换
- 可变分配+全局置换
- 可变分配+局部置换

固定分配：分配的页框数目固定不变

可变分配：可以根据情况增减

局部置换：如果缺页，只能从分配的页框中取出页来置换（这不废话？）

全局置换：从一个空闲物理块队列中取出

### 3.2 调入算法

### 3.3 调入时机

### 3.4 在哪里调，怎么调



`抖动现象`: 刚换入马上就换出，刚换出很快就要换入，太过频繁，是一种很不高效的情况

`工作集`: 某段时间间隔内进程需要访问的页面集合，根据局部性原理，代表了接下来可能会频繁访问的页面集合



`内存映射文件` 

`虚拟存储器性能影响因素`

`地址翻译 `涉及计组的内容





