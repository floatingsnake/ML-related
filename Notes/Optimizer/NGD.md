# Natural Gradient Descent

## Reason

Euclidean Space can't depict parameter space correctly.

Figure below show 2 distribution have same distance under Euclidean Space, but they shouldn't.

!![image.png](https://s2.loli.net/2022/03/07/1SAteRPyEvnUDGL.png)(https://s2.loli.net/2022/03/07/hwpXcUEMRlsfJ1F.png)

## Solution

- Instead of Euclidean Space. Use KL-div to depict parameter space.

![image.png](https://s2.loli.net/2022/03/07/bNJWLI3GtiUDzfc.png)

- FIM(Fisher Information Matrix) 是分布空间的局部曲率

![image.png](https://s2.loli.net/2022/03/07/7mzhJySHjDdQvMZ.png)

- minimize  optimize function.

![image.png](https://s2.loli.net/2022/03/07/Lh7DpXE1rWFVwtG.png)

- using lagrange operator to convert constraint(KL) and using second order tylor to approximate

![image.png](https://s2.loli.net/2022/03/07/MXLIkY3QU6Hd7El.png)

- Derivative of d is 0, then 

![image.png](https://s2.loli.net/2022/03/07/wQuSjpcHqN7Af2K.png)