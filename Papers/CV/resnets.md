# Resnet
## Major 3:
- layers became Deep
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
