## 原码的除法运算

### 不恢复余数法

#### 手算除法(二进制)

> 设机器字长为5位(含1位符号位, n=4), x=0.1011, y=0.1101, 求x/y
> <br> 规律: 忽略小数点, 每确定一位商, 进行一次减法, 得到4位余数, 在余数的末尾补0, 再确定下一位商, 确定5位商即可停止(机器字长为5位)

#### 机器实现

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/original%20code%20division1.drawio.svg)

##### 符号位

符号单独处理: 符号位=Xs⊕Ys

##### 数值位

- 计算机很傻, 会先默认上商1, 如果搞错了再改上商0, 并"恢复余数"
- ACC, MQ整体"逻辑左移". ACC高位丢弃, MQ低位补0

#### 手算实现

##### 恢复余数法

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/IMG/original%20code%20division2.png)

##### 加减交替法(不恢复余数法)

若余数a为负, 则可直接商0, 并让余数左移1位再加上|除数|

![](C:\Users\ricol\Desktop\Computer-Organization-408\Computer-Organization WD\Data representation and operation\IMG\original code division4.png)

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/IMG/original%20code%20division3.png)

##### 区别

- 恢复余数法: 当余数为负时商0, 并+|除数|, 再左移, 再-|除数|
- 加减交替法: 当余数为负时商0, 并左移, 再+|除数|

##### 注意

- 余数的正负性和商相同
- 若余数为负数, 则需要商0, 并+[|y|]补得到正确余数