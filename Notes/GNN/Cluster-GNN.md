# Cluster-GCN:
## 摘要
CGN的SGD训练方法由两个问题：
- 层数增长，导致高**时间**复杂度
- 保持图完整性，导致高**空间**复杂度  

提出了选取**dense subgraph**的**聚类**算法，**限制邻居搜索**。来降低复杂度

## 简介
生成图**节点的embedding**需要**邻居信息**，**本层节点需要上层节点**邻居信息，层数增加，信息数激增

>已经有的GCN算法：
- Full-batch gradient 空间$O(NFL)$**复杂度大,收敛慢**
- Mini-batch SGD 网络深度增加，需要节点信息数**激增**
- VR-GCN 存储所有节点信息，**空间复杂度大**

## Vanilla Cluster-GCN
主要功能是将图划分后，避免层数增加，联系少的邻居节点信息扩张。![image.png](https://i.loli.net/2021/07/12/5r6MQHpbo8dUDKY.png)
算法:
- 将图划分成子图![image.png](https://i.loli.net/2021/07/12/E9mGTNbhRiKwxUF.png)
- 节点embedding矩阵及损失函数
![image.png](https://i.loli.net/2021/07/12/m9nJgAF7EjyPBN4.png)

##  Stochastic Multiple Partitions
### vanilla算法的问题：
- 子图内的边被保留，**子图间的清除**，影响结果
- 相似节点被聚类，导致**簇的分布**与初始数据不同，导致**梯度估计偏差**
  
### Stochastic Multiple Partitions
过程：
- 将图划分为非常多的子图
- 随机取子图组合成一个batch  

## Cluster-GNN最终算法：
![image.png](https://i.loli.net/2021/07/12/DEFxIamRu3qhdsw.png)

### 对训练深层GCN的改进
问题：
- 深层GCN回阻碍前几层网络的信息传递
  
已有解决方法：
- 残差连接![image.png](https://i.loli.net/2021/07/12/wqXd91HpQ6cYgOG.png)

本文提出方法：
思想： 节点周围的邻居影响更大，放大每层邻接矩阵的对角部分
![image.png](https://i.loli.net/2021/07/12/ureFEWfmPQzI5B8.png)