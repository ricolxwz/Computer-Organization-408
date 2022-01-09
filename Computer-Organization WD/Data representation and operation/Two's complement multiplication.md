## 补码的乘法运算

### 补码一位乘法(Booth算法)

#### 原码一位乘法和补码一位乘法的区别

##### 原码一位乘法

- 原码中每次加法可能+0, +[|x|]原
  - MQ中最低位=1时, (ACC)+[|x|]原
  - MQ中最低位=0时, (ACC)+0
- 进行n轮加法, 移位
- 每次移位都是"逻辑右移"
- 符号位不参与运算

##### 补码一位乘法

- 每次加法可能+0, +[x]补, +[-x]补
  - 辅助位-MQ中最低位=1时, (ACC)+[x]补
  - 辅助位-MQ中最低位=0时, (ACC)+0
  - 辅助位-MQ中最低位=-1时, (ACC)+[-x]补
- 进行n轮加法, 移位, 最后再多来一次加法
- 每次移位都是"补码的算数右移"
- 符号位参与运算 
                                                       
#### 机器实现

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Two's%20complement%20multiplication1.drawio.svg)

#### 手算实现

- n轮加法, 算数右移, 加法规则如下:
  - 辅助位-MQ中最低位=1时, (ACC)+[x]补
  - 辅助位-MQ中最低位=0时, (ACC)+0
  - 辅助位-MQ中最低位=-1时, (ACC)+[-x]补
- 补码的算数右移:
  - 符号位不动, 数值位右移, 正数右移补0, 负数右移补1(符号位是啥就补啥)

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/IMG/Two's%20complement%20multiplication2.png)