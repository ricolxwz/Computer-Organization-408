## Cache写策略

### 写命中

#### 写回法(Write-back)

当CPU对Cache写命中时, 只修改Cache的内容, 而不立即写入主存, 只有当此块被换出时才写回主存. 可以增设一个标志位(脏位), 以反映此块是否被CPU修改过

减少了访问次数, 但有数据不一致的隐患

#### 全写法(Write-through)

当CPU对Cache写命中的时候, 必须把数据同时写入Cache和主存, 一般使用写缓冲(Write buffer)

访存次数增加, 速度变慢, 但更能保证数据一致性

使用写缓冲, CPU写的速度很快, 若写操作不频繁, 则效果很好. 若写操作很频繁, 可能会因为写缓冲饱和而发生阻塞. 写缓冲是一个FIFO队列, 写缓冲可以解决速度不匹配的问题.

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/IMG/Cache%20write%20strategy1.png)

### 写不命中

#### 写分配法(Write-allocate)

当CPU对Cache写不命中的时候, 把主存中的块调入Cache, 在Cache中修改, 通常搭配写回法使用.

#### 非写分配法(Not-write-allocate)

当CPU对Cache写不命中时只写入主存, 不调入Cache, 搭配全写法使用

### 多级Cache

现代计算机多采用多级Cache
<br> 离CPU越近的速度越快, 容量越小
<br> 离CPU越远的速度越慢, 容量越大

各级Cache之间通常采用"全写法"+"非写分配法"
<br> Cache-主存之间常采用"写回法"+"写分配法"

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Storage%20System/IMG/Cache%20write%20strategy2.png)