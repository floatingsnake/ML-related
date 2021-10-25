# Noisy Student
## 目的
进行半监督学习，利用上unlabeled的数据
## 过程
![image.png](https://i.loli.net/2021/10/24/dWV8Xetqo6syMTP.png)
![image.png](https://i.loli.net/2021/10/24/fPElBKoMC1I5tyF.png)

## Detial
- Input Noise( on student's input ):
  - **Rand augmentation**:   
        teacher have clean images || student have augmented images
        ![image.png](https://i.loli.net/2021/10/24/xIUT3V82iLg5P4p.png)
- Model Noise( on teacher ):
  - **Dropout**:每个神经元有一定几率被kill掉
  - **stochastic depth** :每层有一定几率被kill掉