# Optimizer
## 历史
> SGD -> SGDM -> NAG ->AdaGrad -> AdaDelta -> Adam -> Nadam
## 优化器框架
![image.png](https://i.loli.net/2021/09/09/IgRQC4NYGiVu5wD.png)
### SGD
随机梯度下降，随机取样本经过计算梯度然后根据学习率下降
- 优点：简单
- 缺点：速度慢，会在沟壑两边震荡，停留在局部最优点
### SGDM
梯度下降中加入惯性，下坡时