#  Augmentation



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

