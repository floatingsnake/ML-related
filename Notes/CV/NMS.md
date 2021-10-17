# NMS（非极大值抑制）

## 应用
解决目标检测中将**检测框重叠**问题  

![image.png](https://i.loli.net/2021/10/14/waUumvSjBCl2L9J.png)

## 背景

Detection Pipeline
![image.png](https://i.loli.net/2021/10/14/TXAo6GqLuytmOx4.png)

## 算法
- **NMS & Soft-NMS** 当选出最大值$b_m$后，检查其他框与$b_m$重合程度，大于阈值就kill掉 || 根据重合程度减弱$score$



![image.png](https://i.loli.net/2021/10/14/9RWFJ5UckMjwPEH.png)
![image.png](https://i.loli.net/2021/10/14/hONafsKwdRZUFkQ.png)

- **Matrix-NMS** 为了使NMS并行计算，用估计来代替循环迭代计算NMS  
 影响Decay的因素
  - 1. The penalty of **each prediction mi on mj (si > sj )**
  - 2. the probability of**mi being suppressed**.
第二个因素是引发串行循环的原因，解决方法如下：
    - the probability has positive correlation with the IoUs. So  we  approximate the probability by the most overlapped prediction on mi
![image.png](https://i.loli.net/2021/10/17/ZsXFmnjkprSxb5i.png)
![image.png](https://i.loli.net/2021/10/17/jYU12CT6KZcnJMq.png)