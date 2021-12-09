## 海明校验码

### 思路简介

- 偶检验: 1010 -> 01010, 能发现奇数位错误, 但无法确定是哪一位出错
- 海明码设计思路: 将信息位分组进行偶检验 -> 多个校验位

### 求解步骤

1. 确定海明吗的位数
2. 确定校验位的分布
3. 求校验位的值
4. 纠错

#### 确定海明码的位数

设n为有效信息位位数, k位校验位位数, 校验位有2^k种状态, 信息位加检验位共n+k位, 出错的情况有n+k种(1位出错), 成功的情况有1种. 所以k和n的关系应该满足: $2^k≥n+k+1$

#### 确定校验位的分布

校验位Pi放在海明位号为$2^{i-1}$的位置上

#### 求校验位的值

将信息位所处的位置转换为二进制数. 将校验位所处的位置理解为权重, 通过异或运算得出校验位的值(基于偶校验)

#### 纠错

将分组中的值进行异或运算, 如果没有出错的话, 得到的结果应该是0(基于偶校验)

### 海明码的检错、纠错能力

- 纠错能力 -- 1位
- 检错能力 -- 2位

> 信息位: 1010
> 1. 确定位数: $2^k≥n+k+1$ n=4 -> k=3
> <br> 设信息位D4D3D2D1, 校验位P3P2P1, 对应的海明码为H7H6H5H4H3H2H1
> 2. 确定校验位的分布
> 
> | H7  | H6  | H5  | H4  | H3  | H2  | H1  |
> | --- | --- | --- | --- | --- | --- | --- |
> | D4  | D3  | D2  | P3  | D1  | P2  | P1  |
> | 1   | 0   | 1   |     | 0   |     |     |
> 3. 求校验位的值
> <br> H3: 3 -> 011
> <br> H5: 5 -> 101
> <br> H6: 6 -> 110
> <br> H7: 7 -> 101
> <br> $P_1=H_3\oplus H_5\oplus H_7=D_1\oplus D_2\oplus D_4=0$
> <br> $P_2=H_3\oplus H_6\oplus H_7=D_1\oplus D_3\oplus D_4=1$
> <br> $P_3=H_5\oplus H_5\oplus H_7=D_2\oplus D_3\oplus D_4=0$
> 
> | H7  | H6  | H5  | H4  | H3  | H2  | H1  |
> | --- | --- | --- | --- | --- | --- | --- |
> | D4  | D3  | D2  | P3  | D1  | P2  | P1  |
> | 1   | 0   | 1   |0    | 0   |1    |0    |
> 4. 纠错
> <br> 校验方程:
> <br> $S_1=P_1\oplus D_1\oplus D_2 \oplus D_4$
> <br> $S_2=P_2\oplus D_1\oplus D_3 \oplus D_4$
> <br> $S_3=P_3\oplus D_2\oplus D_3 \oplus D_4$
> <br> 接收到: 1010010
> <br> $S_1=P_1\oplus D_1\oplus D_2 \oplus D_4=0$
> <br> $S_2=P_2\oplus D_1\oplus D_3 \oplus D_4=0$
> <br> $S_3=P_3\oplus D_2\oplus D_3 \oplus D_4=0$
> <br> 故无错误
> <br> 接收到: 1010000
> <br> $S_1=P_1\oplus D_1\oplus D_2 \oplus D_4=0$
> <br> $S_2=P_2\oplus D_1\oplus D_3 \oplus D_4=1$
> <br> $S_3=P_3\oplus D_2\oplus D_3 \oplus D_4=0$
> <br> 故第010位出错
> <br> ![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/Data%20representation%20and%20operation/IMG/Hamming%20check%20code1.png)
> 5. 全校验位
> <br> S3S2S1=000且全体偶校验成功->无错误
> <br> S3S2S1≠000且全体偶校验失败->有1位错误, 纠正即可
> <br> S3S2S1≠000且全体偶校验成功->有2位错误, 需要重新传输
> 
> | H8  | H7  | H6  | H5  | H4  | H3  | H2  | H1  |
> | --- | --- | --- | --- | --- | --- | --- | --- |
> | P全  | D4  | D3  | D2  | P3  | D1  | P2  | P1  |
> | 1   | 1   | 0   | 1   |0    | 0   |1    |0    |