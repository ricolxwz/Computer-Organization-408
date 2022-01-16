## read only memory ROM

### 了解各种ROM

#### MROM(Mask Read-Only Memory)

掩模式只读存储器: 厂家按照客户需求, 在芯片生产过程中直接写入信息, 之后任何人不得重写(只能读出), 可靠性高, 灵活性差, 生产周期长, 知识和批量定制

#### PROM(Programmable Read-Only Memory)

可编程只读存储器: 用户可用专门的额PROM写入器写入信息, 写一次之后就不可更改

#### EPROM(Erasable Programmable Read-Only Memory)

允许用户写入信息, 之后采用某种方法擦除数据, 可进行多次重写

- UVEPROM(ultraviolet rays): 用紫外线照射8~20分钟, 擦除所有的信息
- EEPROM(第一个E是Electrically): 可用"电擦除"的方式, 擦除特定的字

#### Flash Memory

闪速存储器: 在EEPROM的基础上发展而来, 断电后也能保存信息, 且可进行多次快速的擦除和重写. 由于闪存需要先擦除再写入, 故闪存的"写"的速度要比"读"的速度慢. (U盘, SD卡就是闪存)

#### SSD(Solid State Drives)

固态硬盘: 由控制单元+存储单元(Flash芯片)组成, 与闪速存储器的核心区别在于控制单元不一样, 但存储介质都类似, 可进行多次快速地擦除和重写你, SSD速度快, 功耗低, 价格高. 目前个人电脑常常使用SSD取代传统的机械硬盘(手机辅存也使用Flash芯片, 但是相比SSD使用的芯片集成度高, 功耗低, 价格贵)

### 计算机内的重要ROM

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/SVG/read%20only%20memory%20ROM1.drawio.svg)

主板上的BIOS芯片就是ROM, 通常我们所说的内存条就是"主存", 但事实上, 主板上的ROM芯片也是"主存"的一部分, 逻辑上, 主存由RAM+ROM组成, 且两者常统一编址