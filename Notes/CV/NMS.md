# NMS（非极大值抑制）

## 应用
解决目标检测中将**检测框重叠**问题  

![image.png](https://i.loli.net/2021/10/14/waUumvSjBCl2L9J.png)

## 背景

Detection Pipeline
![image.png](https://i.loli.net/2021/10/14/TXAo6GqLuytmOx4.png)

## 算法
- **NMS** 当选出最大值$b_m$后，检查其他框与$b_m$重合程度，大于阈值就kill掉
- **Soft-NMS** 当选出最大值$b_m$后，检查其他框与$b_m$重合程度，根据重合程度减弱$score$



![image.png](https://i.loli.net/2021/10/14/9RWFJ5UckMjwPEH.png)
![image.png](https://i.loli.net/2021/10/14/hONafsKwdRZUFkQ.png)

- 