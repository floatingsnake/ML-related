# 图神经网络(第一篇)
---
## **简介**

### **图**  是由节点和边两部分组成的一种数据结构。  
>节点包含了实体(entity)信息，边包含实体间的关系(relation)信息  
### **应用**
>- 专注于**图**的应用(graph-focused)  
实值函数R与具体节点无关  **R(G,n) -> 实值**
>- 专注于**节点**的应用(node-focused)  
实值函数R依赖于具体的节点
#### 例子![图建模](https://pic2.zhimg.com/80/v2-ddf5327bbd7f61d2ce762a91e80213b1_1440w.jpg)

## **基本原理** 
### 输入
> 图的节点，边
### 输出
>每个节点处，根据当前**节点状态**分别计算输出
### 更新机制
基于信息传播机制，每一个节点通过相互交换信息来更新自己的节点状态，直到达到某一个稳定值
>![](https://www.zhihu.com/equation?tex=%5Cmathcal%7BL%7D%3D%5Cleft%5C%7B%5Cleft%28%5Cboldsymbol%7BG%7D_%7Bi%7D%2C+n_%7Bi%2C+j%7D%2C+%5Cboldsymbol%7Bt%7D_%7Bi%2C+j%7D%5Cright%29%7C+%5Cboldsymbol%7BG%7D_%7Bi%7D%3D%5Cleft%28%5Cboldsymbol%7BN%7D_%7Bi%7D%2C+%5Cboldsymbol%7BE%7D_%7Bi%7D%5Cright%29+%5Cin+%5Cmathcal%7BG%7D%5Cright.%3Bn_%7Bi%2C+j%7D+%5Cin+%5Cboldsymbol%7BN%7D_%7Bi%7D+%3B+%5Cboldsymbol%7Bt%7D_%7Bi%2C+j%7D+%5Cin+%5Cmathbb%7BR%7D%5E%7Bm%7D%2C+1+%5Cleq+i+%5Cleq+p%2C+1+%5Cleq+j+%5Cleq+q_%7Bi%7D+%5C%7D+%5C%5C)
- **n i,j** 表示节点 
- **t i,j** 表示 期望/标签

#### 更新函数  
>![](https://www.zhihu.com/equation?tex=%5Cbegin%7Barray%7D%7Bl%7D%7B%5Cboldsymbol%7Bx%7D_%7Bn%7D%3Df_%7B%5Cboldsymbol%7Bw%7D%7D%5Cleft%28%5Cboldsymbol%7Bl%7D_%7Bn%7D%2C+%5Cboldsymbol%7Bl%7D_%7B%5Cmathrm%7Bco%7D%5Bn%5D%7D%2C+%5Cboldsymbol%7Bx%7D_%7B%5Cmathrm%7Bne%7D%5Bn%5D%7D%2C+%5Cboldsymbol%7Bl%7D_%7B%5Cmathrm%7Bne%7D%5Cleft%5Bn%5Cright%5D%7D%5Cright%29%7D+%5C%5C+%7B%5Cboldsymbol%7Bo%7D_%7Bn%7D%3Dg_%7B%5Cboldsymbol%7Bw%7D%7D%5Cleft%28%5Cboldsymbol%7Bx%7D_%7Bn%7D%2C+%5Cboldsymbol%7Bl%7D_%7Bn%7D%5Cright%29%7D%5Cend%7Barray%7D%5Clabel%7Beq%3A30%7D+%5C%5C)  
- **Xn**是n节点当前的状态  
**fw**本地转换函数 -> **Fw**是fw的叠加，同理**Gw**  
（节点n的特征向量，邻边的特征向量，邻居的状态，邻居的特征向量）
- **On**是该节点的输出  
**gw**本地输出函数（节点的状态，节点的特征向量）
#### 迭代的形式写更新函数  
>![](https://www.zhihu.com/equation?tex=%5Cbegin%7Baligned%7D+%5Cboldsymbol%7Bx%7D_%7Bn%7D%28t%2B1%29+%26%3Df_%7B%5Cboldsymbol%7Bw%7D%7D%5Cleft%28%5Cboldsymbol%7Bl%7D_%7Bn%7D%2C+%5Cboldsymbol%7Bl%7D_%7B%5Cmathrm%7Bco%7D%5Bn%5D%7D%2C+%5Cboldsymbol%7Bx%7D_%7B%5Cmathrm%7Bne%7D%5Bn%5D%7D%28t%29%2C+%5Cboldsymbol%7Bl%7D_%7B%5Cmathrm%7Bne%7D%5Bn%5D%7D%5Cright%29+%5C%5C+%5Cboldsymbol%7Bo%7D_%7Bn%7D%28t%29+%26%3Dg_%7B%5Cboldsymbol%7Bw%7D%7D%5Cleft%28%5Cboldsymbol%7Bx%7D_%7Bn%7D%28t%29%2C+%5Cboldsymbol%7Bl%7D_%7Bn%7D%5Cright%29%2C+%5Cquad+n+%5Cin+%5Cboldsymbol%7BN%7D+%5Cend%7Baligned%7D+%5C%5C)
- 不动点理论，逼近不动点 x(t+1) = Fw (x(t), l)。进而写出上述更新函数
### 信息传播流图以及等效的网络结构
![](https://pic1.zhimg.com/v2-8cafe036050da7a3a7d8f2fdd86b8ee8_r.jpg)
## 学习方法
### 目标优化函数
![](https://www.zhihu.com/equation?tex=e_%7B%5Cboldsymbol%7Bw%7D%7D%3D%5Csum_%7Bi%3D1%7D%5E%7Bp%7D+%5Csum_%7Bj%3D1%7D%5E%7Bq_%7Bi%7D%7D%5Cleft%28%5Cboldsymbol%7Bt%7D_%7Bi%2C+j%7D-%5Cvarphi_%7B%5Cboldsymbol%7Bw%7D%7D%5Cleft%28%5Cboldsymbol%7BG%7D_%7Bi%7D%2C+n_%7Bi%2C+j%7D%5Cright%29%5Cright%29%5E%7B2%7D+%5C%5C)
### 随机梯度下降优化
- 按照迭代方程迭代 T ​次得到 xn(t)​，此时接近不动点解 x(T) = x
- 计算参数权重的梯度![](https://www.zhihu.com/equation?tex=%5Cpartial+e_%7B%5Cboldsymbol%7Bw%7D%7D%28T%29+%2F+%5Cpartial+%5Cboldsymbol%7Bw%7D)  用基于时间的反向传播算法
- 使用该梯度更新权重W
### 算法流程图
<img src="https://pic3.zhimg.com/80/v2-94558b75354d42e68ef0b998d980cc16_1440w.jpg" style="margin-left:45px" width="190">
  
  - FORWARD用于迭代计算出收敛点
  - BACKWARD用于计算梯度。
### Transition函数实现  
>需要满足**压缩映射**的条件，而且与**不动点**计算相关
#### Linear(nonpositional) GNN
将节点状态方程改为
![](https://www.zhihu.com/equation?tex=%5Cboldsymbol%7Bx%7D_%7Bn%7D%3D%5Csum_%7Bu+%5Cin+%5Ctext+%7B+ne+%7D+%7C+n+%5D%7D+h_%7B%5Cboldsymbol%7Bw%7D%7D%5Cleft%28%5Cboldsymbol%7Bl%7D_%7Bn%7D%2C+%5Cboldsymbol%7Bl%7D_%7B%28n%2C+u%29%7D%2C+%5Cboldsymbol%7Bx%7D_%7Bu%7D%2C+%5Cboldsymbol%7Bl%7D_%7Bu%7D%5Cright%29%2C+%5Cquad+n+%5Cin+%5Cboldsymbol%7BN%7D+%5C%5C)
![](https://www.zhihu.com/equation?tex=h_%7B%5Cboldsymbol%7Bw%7D%7D%5Cleft%28%5Cboldsymbol%7Bl%7D_%7Bn%7D%2C+%5Cboldsymbol%7Bl%7D_%7B%28n%2C+%5Cmathfrak%7Ba%7D%29%7D%2C+%5Cboldsymbol%7Bx%7D_%7Bu%7D%2C+%5Cboldsymbol%7Bl%7D_%7Bu%7D%5Cright%29+%3D+%5Cboldsymbol%7BA%7D_%7Bn%2C+u%7D+%5Cboldsymbol%7Bx%7D_%7Bu%7D%2B%5Cboldsymbol%7Bb%7D_%7Bn%7D+%5C%5C)
#### Nonelinear(nonpositional) GNN
通过惩罚项来保证压缩映射函数
![](https://www.zhihu.com/equation?tex=e_%7B%5Cboldsymbol%7Bw%7D%7D%3D%5Csum_%7Bi%3D1%7D%5E%7Bp%7D+%5Csum_%7Bj%3D1%7D%5E%7Bq_%7Bi%7D%7D%5Cleft%28%5Cboldsymbol%7Bt%7D_%7Bi%2C+j%7D-%5Cvarphi_%7B%5Cboldsymbol%7Bw%7D%7D%5Cleft%28%5Cboldsymbol%7BG%7D_%7Bi%7D%2C+n_%7Bi%2C+j%7D%5Cright%29%5Cright%29%5E%7B2%7D%2B%5Cbeta+L%5Cleft%28%5Cleft%5C%7C%5Cfrac%7B%5Cpartial+F_%7B%5Cboldsymbol%7Bw%7D%7D%7D%7B%5Cpartial+%5Cboldsymbol%7Bx%7D%7D%5Cright%5C%7C%5Cright%29+%5C%5C)
