# GraphSAGE

## 起因
现在方法都是直推式学习，不能泛化到未知节点，即当图的结构改变后，模型失效需要重新学习
>直推式(transductive)学习：从特殊到特殊。在图中学习目标是学习目标是直接生成当前节点的embedding，例如DeepWalk、LINE，把每个节点embedding作为参数，并通过SGD优化，又如GCN，在训练过程中使用图的拉普拉斯矩阵进行计算  

>归纳(inductive)学习：平时所说的一般的机器学习任务，从特殊到一般：目标是在未知数据上也有区分性。即图结构微弱改变后模型不需要动

## 方法
使用提出的**GraphSAGE框架**，特殊在前向传播的过程

### 前向传播
可视化过程见下图，具体过程如下：
1. 对邻居随机采样，控制每一跳的采样数
2. 生成节点Embedding,即聚合邻居信息，由外到内
3. embedding作为$MLP$的输入
![image.png](https://i.loli.net/2021/09/08/UkKXPc8EmtTjoJl.png)

### 聚合函数
1. mean（平均聚合）
2. 归纳聚合，平均聚合后过MLP层
3. LSTM聚合，将邻居embedding输入到LSTM中
4. Pooling聚合，对邻居上层embedding过MLP层，再pooling（mean/max），最后concat，过MLP生成目标embedding

### Loss函数
- 无监督：
  节点embedding靠近邻居，远离非连通点
 ![image.png](https://i.loli.net/2021/09/08/u3Qpan1N7VPrhTx.png)
- 有监督：
 根据具体应用选择Loss，如cross entropy


## 结果
LSTM和Pooling聚合效果好
