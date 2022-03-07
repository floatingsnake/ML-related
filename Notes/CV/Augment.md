#  Augmentation

## Label Smoothing

![image.png](https://s2.loli.net/2022/03/07/DN2ICMymd4ZRb7O.png)

原因：

- 真实标签跟其他标签之间的关系被忽略了，很多有用的知识无法学到；比如：“鸟”和“飞机”本来也比较像，因此如果模型预测觉得二者更接近，那么应该给予更小的loss；
- 倾向于让模型更加“武断”，成为一个“非黑即白”的模型，导致泛化性能差；
- 面对易混淆的分类任务、有噪音（误打标）的数据集时，更容易受影响

## Rotation

- Transform_Matrix

![image.png](https://i.loli.net/2021/11/01/YrnOAoDs7bKV9PX.png)

![image.png](https://i.loli.net/2021/11/01/o9xgNQanbrv3ciA.png)

![image.png](https://i.loli.net/2021/11/01/cTIjmWBK15hbiJf.png)

![image.png](https://i.loli.net/2021/11/01/Na5oslQWEKj4B2V.png)

![image.png](https://i.loli.net/2021/11/01/6XwWhri9sZxbTHl.png)

- cv2.getRotationMatrix2D

  input:  ( center_X, center_Y ), 旋转角度 $\theta$, 缩放比例

  output: Rotation Matrix

  process:  

  1. 将图片平移到(0,0)
  2. 旋转
  3. 图片平移回(center_X,center_Y)

  ![image.png](https://i.loli.net/2021/11/01/imTPvdfoWxbp6Gw.png)

  

- cv2.warpAffine

  input:  Image, Rotation_Matrix, (Weight, Height)

  output:  Image after transformed

  Key Point:

  - images lose info after transformed (会改变目标的大小，特定情况下不用)

  ![image.png](https://i.loli.net/2021/11/01/QSpH5xIsj21VLGh.png)

  - Solution:

    Change Weight , Height

  ​	![image.png](https://i.loli.net/2021/11/01/LtTKFO1d2pXeWDn.png)

