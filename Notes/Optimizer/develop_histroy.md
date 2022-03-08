# Optimizer

## SGD ways
![image.png](https://s2.loli.net/2022/03/08/MvRPwfIKFzNUyHS.png)

## 历史
> SGD -> SGDM -> NAG ->AdaGrad -> AdaDelta -> Adam -> Nadam
## 优化器框架
![image.png](https://i.loli.net/2021/09/09/IgRQC4NYGiVu5wD.png)
### SGD
随机梯度下降，随机取样本经过计算梯度然后根据学习率下降
- 优点：简单
- 缺点：速度慢，会在沟壑两边震荡，停留在局部最优点
### SGDM
为**抑制震荡**，梯度下降中加入惯性，即一阶动量，会保留历史梯度信息(**惯性**)
![image.png](https://i.loli.net/2021/09/09/2nluBLGmNftxaZs.png)

### SGDNA
为避免**局部最优点**，在当前点，根据历史动量预走到下一个点，用下一个点的梯度与累计动量结合生成当前时刻的累计动量
![image.png](https://i.loli.net/2021/09/09/gAzlQhVxeWJCtNb.png)

### AdaGrad
为了对**参数以不同学习率更新**，引入二阶动量，更新频繁的参数，实际学习率会减小
![image.png](https://i.loli.net/2021/09/09/DxNZQEt9KTOkfpR.png)

### AdaDelta
AdaGrad的学习率变化太激进，对于非稀疏的数据，会让实际学习率快速衰减到0，**Delta**将二阶动量从**历史全部梯度**平方和改进为**滑动时间窗口**的梯度平方和
![image.png](https://i.loli.net/2021/09/09/dSJO6PRD2yFrkeh.png)

### Adam
SGDM和AdaDelta的结合版,$Adam = Adaptive + Monmentum$
![image.png](https://i.loli.net/2021/09/09/ZdWPrXNpA3yaSDh.png)

### Nadam
Adam加上NA
![image.png](https://i.loli.net/2021/09/09/LyCUxvRr7TlcPBN.png)