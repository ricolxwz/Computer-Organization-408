## 数据通路的功能&单总线结构

### 数据通路

数据通路的基本结构: 
1. CPU内部单总线方式
2. CPU内部多总线方式
3. 专用数据通路方式

### 数据通路-CPU内部单总线方式

- 内部总线是指同一部件, 如CPU内部连接各个寄存器及运算部件之间的总线
- 系统总线是指同一台计算机系统的各部件, 如CPU、内存、通道和各类I/O接口之间互相连接的总线

#### 寄存器之间的数据传送

比如把PC内容送至MAR, 实现传送操作的流程及控制信号为:
</br> (PC)->Bus PCout有效, PC内容送总线
</br> Bus->MAR MARin有效, 总线内容送MAR
</br> 重要的是描述清楚数据的流向

#### 主存与CPU之间的数据传送

比如CPU从主存读取指令, 实现传送操作的流向及控制信号为: 
</br> (PC)->Bus->MAR PCout和MARin有效, 现行指令地址->MAR
</br> 1->R CU发读命令(通过控制总线发出)
</br> MEM(MAR)->MDR 指令从存储器->数据线->MDR
</br> MDR->Bus->IR MDRout和IRin有效, 现行指令->IR

#### 执行算术或者逻辑运算

比如一条加法指令, 微操作序列及控制信号为: 
</br> Ad(IR)->Bus->MAR MDRout和MARin有效
</br> 1->R CU发出读命令
</br> MEM(MAR)->数据线->MDR 操作数从存储器->数据线->MDR
</br> MDR->Bus->Y MDRout和Yin有效, 操作数->Y
</br> (ACC)+(Y)->Z ACCout和ALUin有效, CU向ALU发送加命令
</br> Z->ACC Zout和ACCin有效, 结果->ACC

### 公共操作

| 时序 | 微操作       | 有效控制信号         |
| ---- | ------------ | -------------------- |
| 1    | (PC)->MAR    | PCout, MARin         |
| 2    | M(MAR)->MDR  | MemR, MARout, MDRinE |
| 3    | (MDR)->IR    | MDRout, IRin         |
| 4    | 指令译码     | -                    |
| 5    | (PC)+1->(PC) | -                    |

