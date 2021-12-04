## 硬件部件

### 主存储器的基本组成

![](https://github.com/Ricolxwz/Computer-Organization/blob/c74d7fc03529c7e1654a4c23379fc502d187f54c/Computer-Organization%20WD/Computer%20system%20overview/IMG/Main%20memory1.png)

- MAR位数反映存储单元的个数
- MDR位数 = 存储字长
- 字和字节是不一样的!

#### 存储体

- 存储单元: 每个存储单元存放一串二进制代码
- 存储元件(存储元): 每个存储单元包含若干存储元件, 每个存储元件存储一位二进制代码
- 存储子: 存储单元中二进制代码的组合
- 存储字长: 存储单元中二进制代码的位数, 应该是8bit的整数倍

### 运算器的基本组成

![](https://github.com/Ricolxwz/Computer-Organization/blob/c74d7fc03529c7e1654a4c23379fc502d187f54c/Computer-Organization%20WD/Computer%20system%20overview/IMG/Arithmetic%20unit1.png)

- 运算器: 用于实现算数运算、逻辑运算
- ACC: 累加器, 用于存放操作数, 或者运算结果
- MQ: 乘商寄存器, 在乘、除运算时, 用于存放操作数或者运算结果
- X: 通用的操作数寄存器, 用于存放操作数
- ALU: 算术逻辑单元, 通过内部复杂的电路实现算数运算、逻辑运算

|                                | 加     | 减         | 乘             | 除           |
| ------------------------------ | ------ | ---------- | -------------- | ------------ |
| ACC(Accumulator)               | 被加数 | 被减数、差 | 乘积高位       | 被除数、余数 |
| MQ(MUltiple-Quotient Register) |        |            | 乘数、乘积低位 | 商           |
| X(Arithmetic and Logic Unit)   | 加数   | 减数       | 被乘数         | 除数         |

### 控制器的基本组成

![](https://github.com/Ricolxwz/Computer-Organization/blob/c74d7fc03529c7e1654a4c23379fc502d187f54c/Computer-Organization%20WD/Computer%20system%20overview/IMG/Controller1.png)

- CU(Control Unit): 控制单元, 分析指令, 给出控制信号
- IR(Instruction Register): 指令寄存器, 存放当前执行的指令
- PC(Program Counter): 程序计数器, 存放下一条指令的地址, 有自动加1的功能

#### 完成一条指令

1. 取指令: PC
2. 存放指令: IR
3. 分析、执行指令: CU

### 计算机的工作过程

![](https://github.com/Ricolxwz/Computer-Organization/blob/c74d7fc03529c7e1654a4c23379fc502d187f54c/Computer-Organization%20WD/Computer%20system%20overview/IMG/work%20process1.png)

1. 最初: (PC)=0, 指向第一条指令的存储地址
2. #1: (PC)->MAR, 导致(MAR)=0
3. #3: M(MAR)->MDR, 导致MDR=000001 0000000101
4. #4: (MDR)->IR, 导致(IR)=000001 0000000101
5. #5: OP(IR)->CU, 指令的操作码送到CU, CU分析后得知, 是“取数”指令
6. #6: Ad(IR)->MAR, 指令的地址码送到MAR, 导致(MAR)=5
7. #8: M(MAR)->MDR, 导致(MDR)=0000000000000010=2
8. #9: (MDR)->ACC, 导致ACC=0000000000000010=2
9. 上一条指令取后PC自动加1, 以上为“取数”指令执行过程. 其他指令自行分析

- M: 主存中某存储单元
- ACC、MQ、X、MAR、MDR: 相应寄存器
- M(MAR): 取存储单元中的数据
- (ACC): 取相应寄存器中的数据
- 指令: 操作码+地址码
- OP(IR): 取操作码
- Ad(IR): 取地址码