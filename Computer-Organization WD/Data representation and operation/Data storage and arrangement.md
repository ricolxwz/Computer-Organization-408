## 数据的存储和排列

### 大小端模式

> 4字节int: 01 23 45 67H -> 19088743D -> 0000 0001 0010 0011 0100 0101 0110 0111B
> <br> 最高有效字节为01(MSB), 最低有效字节为67(LSB)

- 大端模式: 最高的有效字节存储在更低地址的部分, 最低有效字节存储在更高地址的部分(更适合人类阅读)
- 小端模式: 最低的有效字节存储在更低地址的部分, 最高有效字节存储在更高地址的部分(更适合机器存储)

### 边界对齐

现代计算机通常是按字节编址, 即每个字节对应1个地址
<br> 通常也支持按字, 按半字, 按字节寻址
<br> 假设存储字长为32位, 则1个字=32bit, 半字=16bit. 每次访存只能读/写1个字
<br> 字节始终是8位

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/SVG/Data%20storage%20and%20arrangement.drawio.svg)