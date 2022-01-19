## 页式存储器

### 页式存储

一个程序(进程)在逻辑上被分为若干个大小相等的"页面", "页面"的大小与"块"的大小相同. 每个页面可以离散地放入不同的主存块中

### 虚地址vs实地址

- 逻辑地址(虚地址): 程序员视角看到的地址
- 物理地址(实地址): 实际在主存中的地址

> 假设某程序4KB, 操作系统将该程序分为4页, 每页1KB, 要实现取变量x至ACC寄存器
> <br> 机器指令: 000001 001000000011(操作码+地址码, 使用逻辑地址)
> <br> 程序员视角: 整个程序一共4KB=2^12B, 地址范围: 000000000000~111111111111
> <br> 变量x的逻辑地址: 001000000011, 则应该被划分在0号页面中(逻辑页号若干位, 页内地址10位)
> <br> 主存的物理地址一共22位(主存块号12位, 块内地址10位), 变量x的物理地址: 000000000010 10000000011

### 页表: 逻辑页号->主存块号

> |逻辑页号|主存块号|
> |-|-|
> |#0|2|
> |#1|4094|
> |#2|0|
> |#3|4095|
> 
> 变量x的逻辑地址: 001000000011 变量x的物理地址: 000000000010 1000000011

CPU执行的机器指令中, 使用的是"逻辑地址", 因此需要通过"页表"将逻辑地址转化为"物理地址", 页表存储在主存里
<br> 页表的作用: 记录了每个逻辑页面存放在哪个主存块中

### 地址变换过程

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/IMG/page%20memory1.png)

### 地址变换过程(增加TLB)

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/IMG/page%20memory2.png)

注意TLB和Cache的区别: 快表中存储的是页表项的副本; Cache中存储的是主存块的副本

为什么快表很快? -- 因为快表是一种SRAM而内存是一种DRAM, 此外, 快表是一种"相联存储器", 可以按照内容寻访

### 访问过程

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/SVG/page%20memory3.drawio.svg)