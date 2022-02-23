## 数据通路专用通路结构

### 专用数据通路方式-取指周期

![](https://github.com/Ricolxwz/Computer-Organization-408/blob/main/Computer-Organization%20WD/CPU/Data%20Path%20Dedicated%20Path%20Structure.md)

1. (PC)->MAR C0有效
2. (MAR)->主存 C1有效
3. 1->R 控制单元向主存发送读命令
4. M(MAR)->MDR C2有效
5. (MDR)->IR C3有效
6. (PC)+1->PC
7. Op(IR)->CU C4有效