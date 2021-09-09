#RNN
## 简介
循环神经网络（RNN），和BP网络相比，将$X_t$的**输出$O_t$**，作为一个**输入**和$X_{t+1}$同时给到下一个神经元中
## 问题提出
>某些任务需要能够更好的处理序列的信息，即前面的输入和后面的输入是有关系的

## 模型结构
![image.png](https://i.loli.net/2021/07/06/FTdZHCKrjqgbv1J.png)
即隐藏层上一时刻的输出$S$乘以系数$w$返回给隐藏层输入
- 将该结构按照**时序**展开  
![image.png](https://i.loli.net/2021/07/06/Wf7PtocarlDNFVq.png)
![image.png](https://i.loli.net/2021/07/06/A75I8HVSOn64eQh.png)
- $V,W,V$时刻相等（**权重共享**）用于减少计算量
## 学习方法
**BPTT**
- 前向计算出神经元输出
- 反向计算误差项$\delta_i$的值
- 计算梯度
- 随机梯度下降算法更新
## 算法局限性
- 梯度爆炸/消失  
序列较长时，梯度一直传递，变得极大或极小
---
# RNN变体 - LSTM
## 简介  
为了解决梯度消失/爆炸问题，使用长短期记忆的方式（引入门结构），在更长的序列中有好的表现。
## 问题提出
>RNN的梯度爆炸/消失问题严重，尤其在长序列
## 基本结构
![image.png](https://i.loli.net/2021/07/06/SgV9yedGFUzxIAn.png)
由**遗忘门**，输入门，输出门三个部分组成
- 遗忘门
![image.png](https://i.loli.net/2021/07/06/YKF3D5RdAEhjHVP.png)
$$C_t=f_t*C_{t-1}+i_t*\overline C_t$$$f_t$是遗忘门$[0,1]$，控制前一个特征多少被采用，计算方式如下
![image.png](https://i.loli.net/2021/07/06/ZU1kDhiHLR2BtWm.png)
- 输入门
![image.png](https://i.loli.net/2021/07/06/caqBrQMhKJHYnRp.png)
$i_t$是输入门$[0,1]$，控制当前输入有多少被采用，
$\overline C_t$是单元状态的更新值
- 输出门
![image.png](https://i.loli.net/2021/07/06/ij78qxkTl1uGcVt.png)  
$O_t$是输出门，完成节点输出