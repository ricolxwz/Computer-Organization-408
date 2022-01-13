## 加法器&ALU的改进

### 如何更快地产生进位?

$C_i=A_iB_i+(A_i⊕B_i)C_{i-1}$
<br> $C_i=A_iB_i+(A_i⊕B_i)(A_{i-1}B_{i-1}+(A_{i-1}⊕B_{i-1}C_{i-2}))$
<br> $C_i=A_iB_i+(A_i⊕B_i)(A_{i-1}B_{i-1}+(A_{i-1}⊕B_{i-1}(A_{i-2}B_{i-2}+(A_{i-2}⊕B_{i-2})C_{i-3}))$
<br> ...
终有一天可以展开到$C_0$

第i位向更高位的进位可根据被加数, 加数的第1~i位, 再结合C0确定

### 并行加法器的优化

记$G_i=A_iB_i, P_i=A_i⊕B_i$, 可以将上述的式子化简, 得到:
<br> $C_1=G_1+P_1C_0$
<br> $C_2=G_2+P_2C_1=G_2+P_2G_1+P_2P_1C_0$
<br> $C_3=G_3+P_3C_2=G_3+P_3G_2+P_3P_2G_1+P_3P_2P_1C_0$
<br> $C_4=G_4+P_4C_3=G_4+P_4G_3+P_4P_3G_2+P_4P_3P_2G_1+P_4P_3P_2P_1C_0$
<br> ...

并行进位的并行加法器: 各级进位信号同时形成, 又称为先行进位, 同时进位. 但是, 继续套娃会导致电路越来越复杂, 故一般只支持四位进位并行处理, 也就是4位CLA加法器

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Adder&ALU%20Improvements1.drawio.svg)

由4个FA和一些新的线路, 运算逻辑组成

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/IMG/Adder&ALU%20Improvements2.png)

#### 单级先行进位方式(组内并行, 组间串行)

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Adder&ALU%20Improvements3.drawio.svg)

组内进位信号: 
<br> $C_1=G_1+P_1C_0$
<br> $C_2=G_2+P_2C_1=G_2+P_2G_1+P_2P_1C_0$
<br> $C_3=G_3+P_3C_2=G_3+P_3G_2+P_3P_2G_1+P_3P_2P_1C_0$
<br> $C_4=G_4+P_4C_3=G_4+P_4G_3+P_4P_3G_2+P_4P_3P_2G_1+P_4P_3P_2P_1C_0$

记: $G_1^*=G_4+P_4G_3+P_4P_3G_2+P_4P_3P_2G_1; P_1^*=P_4P_3P_2P_1$

$G_1^*$称为组进位产生函数, $P_i^*$称为组进位传递函数. 根据本组的4*2个输入位即可确定本组的$G_1^*$和$P_i^*$

组间传递信号:
<br> $C_4=G_1^*+P_1^*C_0$
<br> $C_8=G_2^*+P_2^*C_4=G_2^*+P_2^*G_1^*+P_2^*P_1^*C_0$
<br> $C_{12}=G_3^*+P_3^*C_8=G_3^*+P_3^*G_2^*+P_3^*P_2^*G_1^*+P_3^*P_2^*P_1^*C_0$
<br> $C_{16}=G_4^*+P_4^*C_{12}=G_4^*+P_4^*G_3^*+P_4^*P_3^*G_2^*+P_4^*P_3^*P_2^*G_1^*+P_4^*P_3^*P_2^*P_1^*C_0$

#### 多级先行进位方式(组内并行, 组间并行)

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Adder&ALU%20Improvements4.drawio.svg)

### ALU芯片的优化

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/IMG/Adder&ALU%20Improvements5.png)