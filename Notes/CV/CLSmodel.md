# Resnet
## Major 3:
- Layers became Deep
- Solving Vanishing Gradient & Exploding Gradient
  - $H(x) = x+f(x)$, 非线性层只需要拟合残差
  - 回传的梯度改变，顶层梯度可以回传到底层
- No extra weight.
  - 恒等映射不增加额外参数

## Detial：
- Relu(x+f(x))
- stack 3\*3 fliter == 5\*5 fliter or others 
![image.png](https://i.loli.net/2021/10/12/lU1FB9rwTCsdfjq.png)

# Densenet
## Major 3:
- 第i层的输出会同时输入到所有下层->加强了特征重用
![image.png](https://i.loli.net/2021/10/12/ytPVSpeNMbsO6vC.png)
- 由DenseBlock和Transition组成
![image.png](https://i.loli.net/2021/10/12/vRI1E7GOxyojSFJ.png)
- 采用bottleneck层来减少计算量

## Detial:
- DenseBlock内部
![image.png](https://i.loli.net/2021/10/12/43C7czXBHsVa2Yf.png)

- 由于**后面层的输入会非常大**，DenseBlock内部可以**采用bottleneck**层来减少计算量

- DenseNet-B,其中 1-1卷积用于降低特征数量
![image.png](https://i.loli.net/2021/10/12/pDOWAGoyFMiLI7j.png)

- Transition层
主要是连接两个相邻的DenseBlock，并且降低特征图大小


# Resnext

## Major 3
- 将 $split-transform-merge$ 融入到resnet中
- 不增加extra参数
- 增加基数很有效

## Detial
- 基本结构
![image.png](https://i.loli.net/2021/10/12/PyQslknUTzCHm32.png)
![image.png](https://i.loli.net/2021/10/12/D5LJm7Kwrhynp6F.png)
将原来的深度为64的卷积核
变成32个深度为4的卷积核组
![image.png](https://i.loli.net/2021/10/12/UCNFX34fG6IHW2n.png)