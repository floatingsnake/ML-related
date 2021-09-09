# Informer-用于长时间预测的Transformer变体
问题：
1，log-sum-exp数值稳定性？
## 用途：
用于长时间细粒度的预测
## Transformer直接用于序列预测
好处
 - 点与点最大路径长度是$O(1)$，梯度回传快，信息保留好

 挑战
 - 自注意力机制的点积运算带来时间复杂度高 $O(L^2*d)$ 
 - 长序列的Input，Encoder/Decoder的堆叠(J层)带来空间复杂度高$O(J.L^2)$
 - 长序列的Output，类似RNN-Based的输出，让inference非常的慢
 ## 解决方案

 ### 问题一 时间复杂度
 可行原因：
 有用的attention只有一少部分
 ![image.png](https://i.loli.net/2021/07/16/tAp24HyiuMmFbVJ.png)
 解决方法：
 用KL散度来算$k,q$的相对熵，评价$q_i$的稀疏性，越大说明这个attention越有用
 ![image.png](https://i.loli.net/2021/07/16/Ed4foPuT1Dz9Rlp.png)
 在Q变成一个Q-bar的稀疏矩阵(用KL评价前n个)
 ![image.png](https://i.loli.net/2021/07/16/7yx9BbzpjgoXV4J.png)
 方案问题:
 - log-sum-exp func有**数值稳定性**问题
 ![image.png](https://i.loli.net/2021/07/16/NDLuHwIxGd7eZR1.png)
- 避免每个点挨个算$M(q^i,K)$，让复杂度仍为$O(L^2)$
取样$Log(L)$个和算整体效果一样  **好狠的证明**
![image.png](https://i.loli.net/2021/07/16/huQkc8VCxRjNMy1.png)

 ### 问题二 输入带来的空间复杂度大
**Distilling**
 做卷积，池化来减少Feature Map
 ![image.png](https://i.loli.net/2021/07/16/NaSQi6KbPWchVz3.png)

### 问题三 输出慢
用Start Token扩展方法，一次性生成所有预测数据。
Start Token是从Input中sample一个与输出等长的数据
![image.png](https://i.loli.net/2021/07/16/NARdPisE7LbV36O.png)