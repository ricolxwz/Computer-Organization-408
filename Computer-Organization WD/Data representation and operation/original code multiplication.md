## 原码乘法运算

### 原码一位乘法

符号单独处理: 符号位=Xs⊕ys, 数值位取绝对值进行乘法计算

实现方法: 先加法再移位, 重复n次

#### 手算实现方法

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/IMG/original%20code%20multiplication2.png)

- 乘数的符号位不参与运算, 可以忽略
- 原码一位乘可以只用单符号位
- 答题时最终结果最好写为原码机器数

原码一位乘法:
<br> 符号位通过异或确定; 数值部分通过被乘数和乘数绝对值的n轮加法, 移位完成. 根据当前乘数中参与运算的位确定(ACC)加什么. 若当前运算位=1, 则(ACC)+[|x|]原; 若当前运算位=0, 则(ACC)+0
<br> 每轮加法后ACC, MQ的内容统一逻辑右移

#### 机器实现方法

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/original%20code%20multiplication1.drawio.svg)