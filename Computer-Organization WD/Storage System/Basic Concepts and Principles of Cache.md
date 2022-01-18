## Cache的基本概念和原理

### 存储系统存在的问题

1. 经过多模块存储器优化后, 存储器的速度和CPU的速度差距依然很大
2. 可以采用更加高速的存储单元设计, 但是会导致存储器的价格上升, 容量下降
3. 故基于程序的局部性原理, 可以增加一个Cache层, 改善"Cache-主存"的层次

### Cache的工作原理

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/SVG/Basic%20Concepts%20and%20Principles%20of%20Cache1.drawio.svg)

实际上, Cache被集成在CPU内部, Cache用SRAM实现, 速度快, 成本高

### 局部性原理

- 空间局部性: 在最近的未来要用到的信息(指令和数据), 很可能与现在正在使用的信息在存储空间上是邻近的(比如说数组元素, 顺序执行的指令代码)
- 时间局部性: 在最近的未来要用到的信息, 很可能是现在正在使用的信息(循环结构的指令代码)

基于局部性原理, 不难想到, 可以把CPU当前访问地址"周围"的部分数据存放到Cache中. 程序B按照"列优先"访问二维数组, 空间局部性更差

### 性能分析

设tc为访问一次Cache所需要的时间, tm为访问一次主存所需要的时间

- 命中率H: CPU欲访问的信息已在Cache中的比率
- 缺失(未命中)率: M=1-H

Cache-主存系统的平均访问时间t为: t=Htc+(1-H)(tc+tm)(先访问Cache, 若Cache未命中再访问主存); 或者t=Htc+(1-H)tm(同时访问Cache和主存, 若Cache命中则立即停止访问主存)

> 假设Cache的速度是主存的5倍, 且Cache的命中率为95%, 则采用Cache后, 存储器性能提高多少(设Cache和主存同时被访问, 若Cache命中则中断访问主存)?
> <br> 设Cache的存取周期为t, 则主存的存取周期为5t
> <br> 若Cache和主存同时访问, 命中时访问时间为t, 未命中时访问时间为5t, 平均访问时间为0.95*t+0.05*5t=1.2t, 故性能为原来的5t/1.2t≈4.17倍
> <br> 若先访问Cache再访问主存, 命中时访问时间为t, 未命中时访问时间为t+5t, 平均访问时间为0.95*t+0.05*6t=1.25t, 故性能为原来的5t/1.25t=4倍

### 有待解决的问题

#### 问题1

基于局部性原理, 不难想到, 可以把CPU目前访问的地址"周围"的部分数据放到Cache中. 如何界定"周围"?

将主存的存储空间"分块", 如:每1KB为一块, 主存和Cache之间以"块"为单位进行数据交换

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/SVG/Basic%20Concepts%20and%20Principles%20of%20Cache2.drawio.svg)

主存的地址共22位: 块号12位, 块内地址10位, 4M=2^22, 1K=2^10, 整个主存被分为2^12=4096块

#### 问题2

如何区分Cache和主存的数据块对应关系? - Cache和主存的映射方式

#### 问题3

Cache很小, 主存很大, 如果Cache满了怎么办? - 替换算法

#### 问题4

CPU修改了Cache中的数据副本, 如何确保主存中数据母本的一致性? - Cache写策略