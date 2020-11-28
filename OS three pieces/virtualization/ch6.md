
# Mechanism: Limited Direct Execution

为了虚拟化CPU，操作系统采用时分复用技术。然而也带来了一些挑战，
比如：
- 性能问题：如何在不增加系统开销的情况下实现虚拟化
- 控制权：如何有效地运行进程，同时保留对CPU的控制，控制权对操作系统尤为重要，因为操作系统负责资源管理。

## 基本技巧：受限直接执行
为了使程序尽可能快地运行，开发人员想出了一种技术：limited direct execution，也即直接在CPU上运行程序即可
- 当OS希望启动程序时，会在进程列表中创建条目，为其分配一些内存，将
程序代码（从磁盘）加载到内存中，找到入口，跳转到那里，开始运行用户代码。

## 问题1：受限制操作
直接执行的优势在于快速。但是，在CPU上直接运行会带来一个问题——如果进程希望执行某种受限操作（比如向磁盘发出I/O请求或者申请更多内存等），应该怎么办?  
设计两种模式：user mode 和 kernel mode
- 硬件通过提供不同的执行模式来协助操作系统。在user mode下，应用程序不能完全访问硬件资源。在kernel模式下，操作系统可以访问机器的全部资源，此外还提供陷入(trap)内核和从陷入返回(return-from-trap)用户模式程序的特别说明和指令。

补充：为什么系统调用看起来像过程调用？  


