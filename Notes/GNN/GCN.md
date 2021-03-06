# GCN
《Semi-Supervied Classification with GCN》
> GCN属于图神经网络GNN的**一类**，是采用**卷积操作**的图神经网络，可以**应用**于图嵌入**GE**
## 图定义
$G=(V,E)$，对每个节点$i$，有特征$x_i$，可用矩阵$X_{N*D}$表示，$N$表示节点数，$D$表示节点的特征数(向量的**维度**)
## 图卷积
### 简介
> 图中的每个结点依靠**邻居和更远的点的影响**而在改变着自己的状态直到最终的**平衡**，关系越亲近的邻居影响越大
###卷积
>**卷积**是通过两个函数f(x)和g(x)生成第三个函数的一种**算子**，它代表的意义是：两个函数中的一个函数如**g(x)**，把g(x)经过**翻转平移**,然后**与f(x)的相乘**，得到的一个新的函数，对这个函数**积分**
$$f(t)*g(t)=\int_{-\infty}^{+\infty}f(\tau)g(t-\tau)d{\tau}=\int_{-\infty}^{+\infty}f(t-\tau)g(\tau)d{\tau}$$
- 就是两个函数进行**傅里叶变换**到频域后做乘积**在做傅里叶逆变换**
$$f*g=F^{-1}\{F\{f\}.F\{g\}\}$$ **数学证明略**
### 拉普拉斯矩阵
将拉普拉斯矩阵进行**特征值分解**，其**特征向量矩阵**用作傅里叶变换的**基**
![image.png](https://i.loli.net/2021/07/14/R5EKzjIt1biT2Ql.png)

**选拉普拉斯矩阵原因：**
- 由于**卷积在傅里叶域的计算简单**，为了在graph上做傅里叶变换，需要**找到graph的连续的正交基对应于傅里叶变换的基**，因此使用拉普拉斯矩阵的特征向量
- 拉普拉斯矩阵是**对称矩阵**，可以进行特征分解

**物理意义**：空间**二阶导**
>求法:
>- **度矩阵**减去**邻接矩阵** 
>$L =D-W$
>- **二阶导**角度 
$L =K_G^{'}K_G^T$  
$K_G$ 表示row是node，col是edge的**矩阵**，值为**度**

### 图卷积公式推导
现在流行的卷积公式，具体卷积方法的历史和变换见[这里](https://blog.csdn.net/yyl424525/article/details/100058264)
![image.png](https://i.loli.net/2021/07/14/CsrvW6OExHMbw7o.png)
把$g$**卷积核**，定义成拉普拉斯矩阵的函数$g(L)$，是可学习的
$U^Tg$整体看成一个可学习的卷积核，可以看成$g_{\theta}(\Lambda)$，于是继续进行推到
![image.png](https://i.loli.net/2021/07/14/f7RmoS9AEhX4qxr.png)


