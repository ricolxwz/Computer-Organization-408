## 主存储器的基本组成

### 基本的半导体元件及原理

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/SVG/The%20basic%20components%20of%20main%20memory1.drawio.svg)

一个内存颗粒上的金属引脚:
1. 地址线
2. 数据线
3. 读写控制线(1个或2个)
4. 片选线(1个)
5. 供电引脚
6. 接地引脚

> 常见的描述: 
> <br> 8K*8位, 即2^13*8bit
> <br> 8K*1位, 即2^13*1bit
> <br> 64K*16位, 即2^16*16bit

### 寻址

总容量为1KB(字长4B):

- 按照字节寻址: 1K个单元, 每个单元1B
- 按字寻址: 256个单元, 每个单元4B
- 按半字寻址: 512个单元, 每个单元2B
- 按双字寻址: 128个单元, 每个单元8B