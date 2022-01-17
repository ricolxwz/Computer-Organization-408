## 双口RAM&多模块存储器

### 存取周期

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/SVG/Dual-port%20ram%20&%20multi-module%20memory1.drawio.svg)

存取周期: 可以连续读/写的最短时间间隔

DRAM芯片的恢复时间比较长, 有可能是存取时间的几倍(SRAM的恢复时间较短), 如DRAM的存取时间为r, 存取周期为T, 则T=4r 

产生的问题: 
1. 多核CPU要访问内存, 怎么办? 
2. CPU的读写速度比主存快很多, 主存恢复时间太长怎么办?

### 双端口RAM

需要有两组完全独立的数据线, 地址线, 控制线. CPU, RAM中也要有更加复杂的控制电路

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/IMG/Dual-port%20ram%20&%20multi-module%20memory2.png)

两个端口对同一主存操作有以下四种情况:
1. 两个端口同时对不同的地址单元存取数据(可以实现)
2. 两个端口同时对同一地址单元读出数据(可以实现)
3. 两个端口同时对同一地址单元写入数据(写入错误)
4. 两个端口同时对同一地址单元, 一个写入数据, 另一个读出数据(读出错误)

解决方法: 置"忙"信号为0, 由判断逻辑决定暂时关闭一个端口(即被延时), 未被关闭的端口正常访问, 被关闭的端口延长一个很短的时间段后再访问

作用: 优化多核CPU访问一根内存条的速度

### 多体并行存储器

> 每个存储体存取周期为T, 存取时间为r, 假设T=4r
> <br> 连续访问: 00000, 00001, 00010, 00011, 00100

为什么要考虑"连续访问"的情况?
<br> 因为在实际应用中, 有很多数据是连续的存储在主存中的, 比如说数组, 程序的指令都是连续的存储在主存中的

#### 高位交叉编址

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/IMG/Dual-port%20ram%20&%20multi-module%20memory3.png)

> 连续取n个存储字
> <br> 耗时nT, 耗时5T

#### 低位交叉编址

宏观上读写一个字的时间接近r

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/IMG/Dual-port%20ram%20&%20multi-module%20memory4.png)

> 耗时T+4r=2T
> <br> 连续存n个存储字
> <br> 耗时T+(n-1)r

### 应该取第几个"体"?

采用"流水线"的方式并行存取(宏观上并行, 微观上串行). 宏观上, 一个存储周期内, m体交叉存储器可以提供的数据量为单个模块的m倍

存取周期为T, 存取时间(总线传输周期)为r, 为了使流水线不间断, 应保证模块的数量m≥T/r:
1. 如果m<T/r, 则会导致CPU需要等待
2. 如果m>T/r, 则会导致芯片闲置

### 多模块存储器

#### 多体并行存储器

每个模块都有相同的容量和存取速度
<br> 各模块都有独立的读写控制电路, 地址寄存器和数据寄存器. 它们既能并行工作, 又能交叉工作.

#### 单体多字存储器

每个存储单元存储m个字
<br> 总线宽度也为m个字
<br> 一次并行读出m个字
<br> 每次只能同时取m个字, 不能单独取其中某个字, 指令和数据在主存中必须是连续存放的

### 内存条

单纯的扩容: 实现高位交叉的多体存储器
双通道: 实现低位交叉的多体存储器

买内存条时, 可挑选相同主频(主频反映的是存取周期, 如果主频不一样, 可能会导致高主频的内存降频), 相同容量(高容量的部分会按单通道处理)的两根来组成双通道