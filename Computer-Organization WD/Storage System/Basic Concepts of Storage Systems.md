## 存储系统基本概念

### 存储器的层次化结构

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/SVG/Basic%20Concepts%20of%20Storage%20Systems1.drawio.svg)


辅存中的数据要调入主存后才被CPU访问

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/SVG/Basic%20Concepts%20of%20Storage%20Systems1.drawio.svg)

有的教材把安装在电脑内部的磁盘称为"辅存", 把U盘, 光盘等称为"外存". 也有的教材把磁盘, U盘, 光盘等统称为"辅存"或者"外存"

- 主存-辅存: 实现虚拟操作系统, 解决了主存容量不够的问题
- Cache-主存: 解决了主存与CPU速度不匹配的问题

### 存储器的分类

#### 按照层次

- 高速缓存(Cache)
- 主存储器(主存, 内存)
- 辅助存储器(辅存, 外存)

#### 存储介质

- 半导体存储器(主存, Cache)
- 磁表面存储器(磁盘, 磁带)
- 光存储器(光盘, DVD)

#### 存取方式

- 随机存取存储器(Random Access Memory, RAM): 读写任何一个存储单元所需的时间都相同, 与存储单元所在的物理位置无关
- 顺序存取存储器(Sequential Access Memory, SAM): 读写一个存储单元所需的时间取决于存储单元所在的物理位置
- 直接存取存储器(Direct Access Memory, DAM): 既有随机存取特性, 也有顺序存储的特性. 先直接选取信息所在的区域, 然后按照顺序方式存取
- 相联存储器(Associative Memory), 即可以按内容访问的存储器(Content Addressed Memory, CAM), 可以按照内容检索到存储位置进行读写, "快表"就是一种相联存储器

串行访问存储器: 读写某个存储单元所需的时间和存储单元的物理位置有关, 上述SAM和DAM就是串行访问存储器

RAM, SAM和DAM是按照地址来访问, CAM是按照内容来访问

#### 信息的可更改性

- 读写存储器(Read/Write Memory) -- 既可读, 也可写(如: 磁盘, 内存, Cache)
- 只读存储器(Read Only Memory) -- 只能读, 不能写(如: 实体音乐专辑通常采用的CD-ROM, 实体电影中采用的蓝光光碟, BIOS通常写在ROM中)

#### 信息的可保存性

- 断电后, 存储信息消失的存储器 -- 易失性存储器(主存, Cache)
- 断电后, 存储信息依然保持的存储器 -- 非易失性存储器(磁盘, 光盘)

- 信息读出后, 原存储信息被破坏 -- 破坏性读出(如DRAM芯片, 读出数据后要进行重写)
- 信息读出后, 原存储信息不会被破坏 -- 非破坏性读出(如SRAM芯片, 磁盘, 光盘)

### 存储器的性能指标

- 存储容量: 存储字数*字长
- 单位成本: 每位价格=总成本/总容量
- 存储速度: 数据传输率=数据的宽度/存储周期

1. 存储时间(Ta): 存取时间指的是从启动一次存储器操作到完成该操作所经历的时间, 分为读出时间和写入时间
2. 存取周期(Tm): 存取周期又称为读写周期或者访问周期, 它是指存储器进行一次完整的读写操作所需要的全部时间, 即连续两次独立地访问存储器操作(读或写操作)之间所需要的最小时间间隔

主存带宽(Bm): 主存带宽又称为数据传输率, 表示每秒从主存进出信息的最大数量, 单位为字/秒, 字节/秒或者位/秒