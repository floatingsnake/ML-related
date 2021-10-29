#  Deep Interest Network for CTR

## 结构

![image.png](https://i.loli.net/2021/10/29/wL9jW8Jt7dKSoV2.png)

## Major：

- attention机制，在将embedding聚合的时候，给予**不同的权值**

  ![image.png](https://i.loli.net/2021/10/29/DjqbyVCmXWTgd8Z.png)

- 改进L2正则化，降低高维稀疏输入在计算L2时的复杂度

![image.png](https://i.loli.net/2021/10/29/rgJ2awjtqOvlMXn.png)

- 改进激活函数，修正输入的分布

![image.png](https://i.loli.net/2021/10/29/RFCaTmAfwkIU6M9.png)

![image.png](https://i.loli.net/2021/10/29/DUKdObJNQyRgXhi.png)

