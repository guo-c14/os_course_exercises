# lec1: 操作系统概述

---

## **提前准备**

（请在上课前完成）

* 完成lec1的视频学习和提交对应的在线练习
* git pull ucore\_os\_lab, ucore\_os\_docs, os\_tutorial\_lab, os\_course\_exercises in github repos。这样可以在本机上完成课堂练习。
* 知道OS课程的入口网址，会使用在线视频平台，在线练习/实验平台，在线提问平台\(piazza\)
  * [http://os.cs.tsinghua.edu.cn/oscourse/OS2019spring](http://os.cs.tsinghua.edu.cn/oscourse/OS2019spring)


* 会使用linux shell命令，如ls, rm, mkdir, cat, less, more, gcc等，也会使用linux系统的基本操作。
* 在piazza上就学习中不理解问题进行提问。



# 思考题

## 填空题

* 当前常见的操作系统主要用 __C/C++与汇编__ 编程语言编写。
* "Operating system"这个单词起源于 __"Operator"__ 。
* 在计算机系统中，控制和管理 __各种资源__ 、有效地组织 __多道程序__ 运行的系统软件称作 __操作系统__ 。
* 允许多用户将若干个作业提交给计算机系统集中处理的操作系统称为 __批处理__ 操作系统。
* 你了解的当前世界上使用最多的操作系统是 __Android__ 。
* 应用程序通过 __系统调用__ 接口获得操作系统的服务。
* 现代操作系统的特征包括 __并发性__ ， __共享性__ ， __虚拟性__ ， __异步性__ ， __持久性__ 。
* 操作系统内核的架构包括 __宏内核__ ， __微内核__ ， __外核__ 。


## 问答题

- 请总结你认为操作系统应该具有的特征有什么？并对其特征进行简要阐述。

~~1. 并发：计算机系统中同时存在多个运行的程序，需要操作系统管理和调度；~~

~~2. 共享：多个应用并发运行的时候，宏观上要体现出它们同时在访问资源，微观上要实现它们的互斥访问；~~

~~3. 虚拟：通过交替运行让每个用户都感到整个计算机在专门为其服务；~~

~~4. 异步：程序执行不是一贯到底，而是走走停停，向前推进的速度不可预知，操作系统要保证只要运行环境相同，程序运行的结果就相同。~~


1. 并发性：并发是指两个或多个事件在同一时间间隔内发生，在多道程序环境下，一段时间内宏观上有多个程序在同时执行，而在同一时刻，单处理器环境下实际上只有一个程序在执行，故微观上这些程序还是在分时的交替进行。操作系统的并发是通过分时得以实现的。操作系统的并发性是指计算机系统中同时存在多个运行着的程序，因此它具有处理和调度多个程序同时执行的能力；
2. 共享性：系统中的资源可供内存中多个并发执行的进程共同使用；
3. 虚拟性：虚拟是指把一个物理上的实体变为若干个逻辑上的对应物。在操作系统中利用了多种虚拟技术，分别用来实现虚拟处理器、虚拟内存和虚拟外部设备；
4. 异步性：在多道程序环境下，允许多个程序并发执行，但由于资源有限，进程的执行不是一贯到底，而是走走停停，以不可预知的速度向前推进，这就是进程的异步性。异步性使得操作系统运行在一种随机的环境下，可能导致进程产生于时间有关的错误。但是只要运行环境相同，操作系统必须保证多次运行进程，都获得相同的结果；
5. 持久性：通过实现文件系统，操作系统可以将程序以及数据存储在磁盘等存储介质中。

- 为什么现在的操作系统基本上用C语言来实现？为什么没有人用python，java来实现操作系统？

~~因为C是最接近底层的高级语言，编译器可以很容易将C转换为高效的机器代码，并且编码人员对这种转换是比较清楚的，C语言在能描述清楚底层硬件的同时足够的高级、成熟、高效；python和java本身需要特定的运行环境，不够底层和高效。~~

C语言是编译型语言，有良好的性能，能够直接嵌入汇编，可以方便地操作硬件；Python，Java无法保证性能，不能直接操作硬件。

---

## 可选练习题

---

- 请分析并理解[v9\-computer](https://github.com/chyyuu/os_tutorial_lab/blob/master/v9_computer/docs/v9_computer.md)以及模拟v9\-computer的em.c。理解：在v9\-computer中如何实现时钟中断的；v9 computer的CPU指令，关键变量描述有误或不全的情况；在v9\-computer中的跳转相关操作是如何实现的；在v9\-computer中如何设计相应指令，可有效实现函数调用与返回；OS程序被加载到内存的哪个位置,其堆栈是如何设置的；在v9\-computer中如何完成一次内存地址的读写的；在v9\-computer中如何实现分页机制。

- 请编写一个小程序，在v9-cpu下，能够输出字符

- 输入的字符并输出你输入的字符

- 请编写一个小程序，在v9-cpu下，能够产生各种异常/中断

- 请编写一个小程序，在v9-cpu下，能够统计并显示内存大小

- 请分析并理解[RISC-V CPU](http://www.riscvbook.com/chinese/)以及会使用模拟RISC\-V(简称RV)的qemu工具。理解：RV的特权指令，CSR寄存器和在RV中如何实现时钟中断和IO操作；OS程序如何被加载运行的；在RV中如何实现分页机制。
  - 请编写一个小程序，在RV下，能够输出字符
  - 输入的字符并输出你输入的字符
  - 请编写一个小程序，在RV下，能够产生各种异常/中断
  - 请编写一个小程序，在RV下，能够统计并显示内存大小

## 参考资料
 - [Intel格式和AT&T格式汇编区别](http://www.cnblogs.com/hdk1993/p/4820353.html)
 - [x86汇编指令集  ](http://hiyyp1234.blog.163.com/blog/static/67786373200981811422948/)
 - [PC Assembly Language, Paul A. Carter, November 2003.](https://pdos.csail.mit.edu/6.828/2016/readings/pcasm-book.pdf)
 - [*Intel 80386 Programmer's Reference Manual*, 1987](https://pdos.csail.mit.edu/6.828/2016/readings/i386/toc.htm)
 - [IA-32 Intel Architecture Software Developer's Manuals](http://www.intel.com/content/www/us/en/processors/architectures-software-developer-manuals.html)
 - [v9 cpu architecture](https://github.com/chyyuu/os_tutorial_lab/blob/master/v9_computer/docs/v9_computer.md)
 - [RISC-V cpu architecture](http://www.riscvbook.com/chinese/)
 - [OS相关经典论文](https://github.com/chyyuu/aos_course_info/blob/master/readinglist.md)
