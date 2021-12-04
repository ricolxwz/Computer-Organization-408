## 计算机的层次结构

### 层次结构

![](https://github.com/Ricolxwz/Computer-Organization/blob/627156e24c745225017b428b6e95285180c849f5/Computer-Organization%20WD/Computer%20system%20overview/IMG/Multi-level%20hierarchical%20structure%20of%20computer%20system1.png)

- M0: 由硬件直接执行微指令
- M1: 执行二进制机器指令
- M2: 向上提供“广义指令”, 由操作系统程序实现, 由机器指令和广义指令组成, 目的是为了扩展机器功能, 也称为混合层
- M3: 用汇编程序翻译成机器语言程序
- M4: 用编译程序翻译成汇编语言程序

### 三种级别的语言

![](https://github.com/Ricolxwz/Computer-Organization/blob/main/Computer-Organization%20WD/Computer%20system%20overview/IMG/Computer%20hierarchy1.png)

#### 编译程序和解释程序的区别

- 编译程序: 将高级语言编写的源程序全部语句一次全部翻译成机器语言程序, 而后再执行机器语言程序(只需要翻译一次)
- 解释程序: 将源程序的一条语句翻译成对英语机器语言的语句, 并立即执行. 紧接着再翻译下一句(每次执行都需要翻译)