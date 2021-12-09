## 计算机硬件的基本组成

### 冯诺依曼结构

#### 存储程序

- 存储程序: 指将指令以二进制代码的形式事先输入计算机的主存储器, 然后按其在存储器中的首地址执行程序的第一条命令, 以后就按该程序的规定顺序执行其他的命令, 直至程序执行结束

#### 流程

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Computer%20system%20overview/IMG/The%20basic%20composition%20of%20computer%20hardware1.png)

#### 特点

1. 计算机由五大部件组成: I/O设备、存储器、运算器、控制器
2. 指令和数据以同等地位位于存储器, 可以按地址寻访
3. 指令和数据用二进制表示
4. 指令由操作码和地址码组成
5. 存储程序
6. 以运算器为中心(输入/输出设备与存储器之间的数据传送通过运算器完成)

### 现代计算机的结构

- 以存储器为中心
- CPU = 运算器 + 控制器
  
#### 流程

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Computer%20system%20overview/IMG/The%20basic%20composition%20of%20computer%20hardware2.png)

- “主机”指的是CPU+主存储器
- “辅存”指的是机械硬盘等等

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Computer%20system%20overview/IMG/The%20basic%20composition%20of%20computer%20hardware3.png)

### 存储器的层次结构

- 寄存器: CPU中的存储器, 少量但是速度很快
- 高速缓冲存储器: 介于CPU和主存之间, 称为“Cache”
- 主存: 即通常所说的内存条