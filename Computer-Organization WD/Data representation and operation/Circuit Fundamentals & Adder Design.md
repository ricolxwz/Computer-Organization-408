## 电路基本原理&加法器设计

### 算数逻辑单元(ALU)

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Circuit%20Fundamentals%20&%20Adder%20Design1.drawio.svg)

### 最基本的逻辑运算

- $A(C+D)=AC+AD$ --- 分配律
- $ABC=A(BC)$ --- 结合律
- $A+B+C=A+(B+C)$ --- 结合律

#### "与"

$Y=A·B$

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

#### "或"

$Y=A+B$

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 1   |

#### "非"

$Y=\overline{A}$

| A   | Y   |
| --- | --- |
| 0   | 1   |
| 1   | 0   |

### 复合逻辑运算

- $\overline{A+B}=\overline{A}\cdot \overline{B}$
- $\overline{A\cdot B}=\overline{A}+\overline{B}$ 

#### "与非"

$Y=\overline{A·B}$

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |

#### "或非"

$Y=\overline{A+B}$

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 0   |

#### "异或"

$Y=A⊕B=\overline{A}\cdot B+A\cdot \overline{B}$

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |

#### "同或"

$Y=A⊙B$

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

### 一位全加器(FA, full adder)

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Circuit%20Fundamentals%20&%20Adder%20Design3.drawio.svg)

#### 输入

$A_i, B_i, C_{i-1}$

#### 输出

- $S_i=A_i⊕B_i⊕C_{i-1}$: 输入有奇数个1时为1(异或)
- $C_i=A_iB_i+(A_i⊕B_i)C_{i-1}$: 输入中至少2个1(两个为都是1或者两个本位中有一个是1, 且来自低位的进位是1)

#### 电路设计

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/IMG/Circuit%20Fundamentals%20&%20Adder%20Design2.png)

### 串行加法器

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Circuit%20Fundamentals%20&%20Adder%20Design4.drawio.svg)

- 只有一个全加器, 数据逐位串行送入加法器中进行运算. 进位触发器用来寄存进位信号, 以便参与下一次运算.
- 如果操作数长n位, 加法就要分为n次进行, 每次产生一位和, 并且串行逐位送回寄存器

### 并行加法器

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Circuit%20Fundamentals%20&%20Adder%20Design5.drawio.svg)

- 该种并行加法器称为串行进位的并行加法器
- 把n个全加器串接起来, 就可进行两个n位数的相加
- 串行进位又称为行波进位, 每一级进位直接依赖于前一级的进位, 即进位信号是逐级形成的