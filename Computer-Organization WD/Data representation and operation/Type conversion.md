## 强制类型转换

### 代码

```c
void main() {
    short x = -4321; // short类型占用2个字节, x: 1110 1111 0001 1111
    unsigned short y = (unsigned short)x; // 会将x的二进制数值完整地复制给y, y的值为1110 1111 0001 1111, 真值为61215. 无符号数与有符号数, 不改变数据内容, 改变解释方式
    int a = 165537, b = -34991; // int型占用4个字节, a:0x000286a1, b:0xffff7751
    short c = (short)a, d = (short)b; // short型占用2个字节, 长整数变短整数: 高位截断, 保留低位, c:0x86a1, 真值:-31071; d:0x7751, 真值:30545
    short x = -4321; // x:1110 1111 0001 1111 x:0xef1f
    int m = x; // m:1111 1111 1111 1111 1110 1111 0001 1111 m:0xffffef1f 真值:-4321
    unsigned short n = (unsigned short)x; // n:1110 1111 0001 1111 0xef1f 真值:61215
    unsigned int p = n; // p:0000 0000 0000 0000 1110 1111 0001 1111 0x0000ef1f 真值61215
}
```