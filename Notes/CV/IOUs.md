# IOU-S

##  IoU

![image.png](https://i.loli.net/2021/10/29/WFKwmDzdfIa51xY.png)

## 

<img src="https://i.loli.net/2021/10/29/QitIEvoCafskWqe.png" alt="image.png"  />



## G-IoU

- 减轻当gt和pb**不重叠**时的**梯度消失**问题
-  C 是包含B和B gt的最小box
- 右侧项表示最小框的空白占比

![image.png](https://i.loli.net/2021/10/29/RJHFlrUci23Z17N.png)

## D-IoU

- 右侧项表示pd和gt的欧氏距离

![image.png](https://i.loli.net/2021/10/29/EJIMu5PrjwZG4be.png)

##  C-IoU

-  α 是平衡常数
- v 是pd和gt的长宽比
- 为避免梯度爆炸，自定了求导

![image.png](https://i.loli.net/2021/10/29/b1zRMmvFXgGaSHt.png)

![image.png](https://i.loli.net/2021/10/29/z2MUHZEhkBbri5v.png)

![image.png](https://i.loli.net/2021/10/29/cE5kGWKOXa9ZYVv.png)

![image.png](https://i.loli.net/2021/10/29/fScYmOMa7A1x2on.png)