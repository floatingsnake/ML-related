Base on Binary classification problem

## Loss
>MSE make Loss Function not-**convex**
![image.png](https://i.loli.net/2021/09/11/vKsUEXkiJj3MA9l.png)
Gradient Descent would stuck **local optimum**

>Entrop works well
![image.png](https://i.loli.net/2021/09/11/o5964d2SmahRZUV.png)
as y=1, make $\hat{y}$ larger
asy=0, make$\hat{y}$ smaller
![image.png](https://i.loli.net/2021/09/11/twJSiBsguRXyLNY.png)
$\frac{\partial{J(w,b)}}{\partial{w}}$ means ${J(w,b)}$has more than 1 variables
$\frac{d{J(w,b)}}{d{w}}$ means ${J(w,b)}$has 1 variable

## Computation Graph
![image.png](https://i.loli.net/2021/09/11/D9q1GJWCHA45oOk.png)

## Vectorization
Vectorize is much faster! 
Related to **Computer Archtecture** Knowledge!

## Broadcasting
expand in rows or columns
![image.png](https://i.loli.net/2021/09/11/4MBJTU9grXREdCa.png)

## Activation Functions

- Sigmoid
  - hardly use except **output**
    ![image.png](https://i.loli.net/2021/09/11/FamNTMgA4h2p5Q8.png)

- tanh
  - Works better than Sigmoid
    - center data -> mean(data)=0
    ![image.png](https://i.loli.net/2021/09/11/ZyvIEqlXiJ91ar8.png)

For above ,when **Z is large**, gradient of derivative is very **Small**
In the following, Z is large, Gradient is large. so learn **faster**
- Relu
  - when z<0 slap=0, in practive is OK because most of time, Enough hidden units would make z > 0
    ![image.png](https://i.loli.net/2021/09/11/HLW8jq5xBVUpXdY.png)
- LeakyRelu
- ![image.png](https://i.loli.net/2021/09/11/PQpDHIalbNo3hFZ.png)