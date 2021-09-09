# GNN用于多元时间序列预测
## 摘要
多元时间序列分析重点在变量间的依赖分析。图这种结构很适合，但普通GNN需要明确定义图的结构，不能直接应用。本文提出了一个通用框架，可以**生成单向关系**，提取时间空间的关联。

## 简介
简单提及三种方法VAR，GP，LSTNet在多元时间序列分析的应用。  

### 在多元时序分析使用GNN的**问题**：  
- 图的结构未知
- 大多数GNN只关注消息传递，忽略图结构变化（网络难以收敛）

### 本文重点
- 第一个从GNN角度处理多元时序分析
- 提出新的学习模块来学习变量间的依赖关系
- 提出了一个多元时序分析，学习机制的框架
- 在四个数据集上做对比实验，效果优异
## 问题定义
**输入**：  
- 时间序列数据+辅助数据
$ \chi=\{S_{t1},S_{t2},...,S_{tp}\}$  
$S_{ti} = z_{ti} +au_{ti}$
$au_{ti}$为辅助数据，如日期，季节等  

**输出**：
- 序列数据预测
$ Y = \{z_{tp+1},z_{tp+2},...,z_{tp+q}$\}

**目标**：
- 寻找函数$f(.)$产生从X到Y的映射


## MTGNN框架
### 概括框架
![QQ截图20210705161956.png](https://i.loli.net/2021/07/05/Fd8mGZxkwogjVQK.png)
整个框架分为四个部分
- 图结构学习
- 图卷积
- 时间卷积
- 输出预测结果

### 详细框架  
![1.png](https://i.loli.net/2021/07/05/dAvNaX62KlHYz3s.png)
- 图学习层学到序列数据的邻接矩阵$A_{ij}$
- 图卷积和时间卷积交替存在输出，用于捕捉时间和空间的依赖关系
- Residual连接和skip连接用于避免梯度消失问题
#### 图学习层  
邻接矩阵动态学习
![image.png](https://i.loli.net/2021/07/05/i5DBHZNGKzgYFE9.png)
- $E_i$表示随机选择的节点
- $\Theta_i$是模型的参数
- $argotopk(.)$表示取前K个边，目的是减少计算量

#### 图时间卷积
(Red:Time Blue:Graph)
![image.png](https://i.loli.net/2021/07/05/WGiVErOYIubQeND.png)
##### 图卷积模块
![image.png](https://i.loli.net/2021/07/05/4HNLluWwXKZocA3.png)  
(a)由两个(b)输出相加得到
**Mix-Hop层 (b)**  
由信息传输和信息选择两个部分组成
- 信息传输  
![image.png](https://i.loli.net/2021/07/05/PNuA1rwk5GtfMIF.png)
- 信息选择
![image.png](https://i.loli.net/2021/07/05/AUTJEGKsmR4DBcO.png)  

##### 时间卷积模块
![image.png](https://i.loli.net/2021/07/05/di51DGHEcswaSI9.png)
- (a)tanh作为过滤器，sigmoid作为门控制进入下一层的信息
- (b)扩展层卷积核使用2,3,6,7更好组合适用于一般的周期7,12,24,28,60等    

##### 感受野
![image.png](https://i.loli.net/2021/07/05/QwqapKk56HNnYim.png)
- R为感受野大小
- m为卷积网络层数，c为核的大小

为了降低模型复杂度，采用**扩张感受野**的方法
![image.png](https://i.loli.net/2021/07/05/qoxpD1zk5ZVvYTe.png)
- q是扩张速度，由扩张因子决定，采样步数增大

#### 学习算法  
![image.png](https://i.loli.net/2021/07/05/UITgeWPYoxG4SFV.png)
>特点：
>- 为了降低空间复杂度，每次随机将节点分组，然后算组之间的$A_{ij}$
>- 采用课程学习策略，即解决问题由简单到复杂。开始只预测一步，迭代增加预测长度