# 注意力机制及Transformer模型

## self_attention
只有$W^{qkv}$需要学习出来的
![image.png](https://i.loli.net/2021/07/16/DhbpiKs6IYu4xO5.png)
![image.png](https://i.loli.net/2021/07/16/QlVMUDcfy5Gn4p7.png)
![image.png](https://i.loli.net/2021/07/16/m4wkqaGfRJBzcQH.png)
![image.png](https://i.loli.net/2021/07/16/81SzwsJ4Vby29Qr.png)
![image.png](https://i.loli.net/2021/07/16/ngTOztkyDw7XZLo.png)

## mult-head self attention
对**不同层次的相似度**进行捕捉
对每个qkv乘以两个矩阵，变成q1,q2,k1,k2,v1,v2，分别来计算。
![image.png](https://i.loli.net/2021/07/16/za3WlLuQe27hoIB.png)
## 问题:计算量太大
## 问题:无位置咨询
解决:加一个位置向量(这篇文章使用sin,cos完成的)
![image.png](https://i.loli.net/2021/07/16/uFP3MWgy7V6U4pf.png)

- self-attention是CNN的泛化
- self-attention和RNN对比
![image.png](https://i.loli.net/2021/07/16/NWMRBjzaCJ3O6lF.png)

## Self-attention for Graph
把$Attention Martix$只算邻接矩阵中的注意力评估

## Seq2Seq
![image.png](https://i.loli.net/2021/07/16/TNgSZah16c2EqHr.png)
### Encoder-transfomer
![image.png](https://i.loli.net/2021/07/16/iVT3XNOZDWcthpH.png)
![image.png](https://i.loli.net/2021/07/16/eYwQvo7iAb92RXu.png)
- *Batch Normalization* 是对这批样本的同一维度特征做归一化 
-  *Layer Normalization* 是对这单个样本的所有维度特征做归一化
### Decoder-transfomer
#### Autoregressive
![image.png](https://i.loli.net/2021/07/16/zDibA2VTyjFfwZg.png)
![image.png](https://i.loli.net/2021/07/16/P9EtWcaUyDsIM2H.png)
![image.png](https://i.loli.net/2021/07/16/38YPGbvfUo4mI2X.png)
![image.png](https://i.loli.net/2021/07/16/FapSxCErMoKIyWU.png)
**mask_self attention**
![image.png](https://i.loli.net/2021/07/16/URiM9bjDvc1NuIL.png)