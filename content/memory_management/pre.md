---
title: 前置知识 
---

# 前置基础

## 1 链接和装入

源程序变成可执行文件的过程：

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230527185816126.png" alt="image-20230527185816126.png" style="zoom:40%;" />

可执行文件要被调入内存种才能执行，这个过程叫`装入`

链接有三种方式：

装入也有三种方式

## 2 地址

`逻辑地址`：编译后每个模块都是从0开始编址的相对地址

而链接程序将两个模块合并时就需要修改相对地址，但也只是相对一个0，还是相对地址

内存运行计算时直接使用的也还是逻辑地址

逻辑地址经过地址变换转为物理地址才能在内存种找到相应的位置，这叫`地址重定位`

具体来说是有一种`页表`，它记录了对应关系，由操作系统维护，处理器使用它

## 3 内存映像

程序调入内存并运行，形成了进程在的内存种的实体，这个叫`内存映像`，实体=映像

具体来说分成几段：

- 代码段、数据段
- PCB，没错之前说的PCB就是保存在内存中
- 堆：存放动态分配的变量
- 栈：用以实现函数调用，从高向低增长

比如第一个进程如果完整放入内存应该是这样子：

{{< details "内存映像">}}
<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230529164641332.png" alt="image-20230529164641332" style="zoom:47%;" />
{{< /details >}}

## 4 内存保护、共享

就是避免越界访问，需要一个检查装置

...