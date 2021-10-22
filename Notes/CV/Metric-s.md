# Object Detection Metric

## Basic 
- IOU  
![image.png](https://i.loli.net/2021/10/20/uiAwneoU1bMkDEB.png)
- TP(True Positive):  
**correct detection** of a **ground-truth** bounding box
- FP(False Positive):  
**incorrect detection** of a **non-existing** object or a **misplaced**
detection of an existing object
- FN(False Negative):  
**undetected ground-truth**bounding box
- Precision & Recall  
![image.png](https://i.loli.net/2021/10/20/TY5uPwI81WEx9lU.png)

## Metrics

- **AP(average precision)**：在pr曲线上，对precision求离散积分均值
  ![image.png](https://i.loli.net/2021/10/20/HmJ8IZbjT4keO6d.png)
  - 插值，每次选取右侧最大值
  ![image.png](https://i.loli.net/2021/10/20/jy1Ymlc6nV2RKxI.png) 
  - N-Point插值
  ![image.png](https://i.loli.net/2021/10/20/sPHy9O76S5WV8pk.png)
  - All-Point插值法:· 算P-R曲线的下面的面积
  ![image.png](https://i.loli.net/2021/10/20/uY4AtXJjBpbDcfn.png)
  - 算均值  
  ![image.png](https://i.loli.net/2021/10/20/OKir53jAbphL9Yt.png)

- **mAP(Mean Average Precision)**: 多类别取ap均值
  ![image.png](https://i.loli.net/2021/10/20/AiBORralCgNjQXV.png)

- **AR(average Recall)**: IOU在0.5~1的recal均值的2倍
  ![image.png](https://i.loli.net/2021/10/20/Q21BuYJdcnF9vot.png)
  ![image.png](https://i.loli.net/2021/10/20/7RwgcLK5W6XMSFf.png)

**mAR(Mean Average Recall)**: 多类别取ar均值
  ![image.png](https://i.loli.net/2021/10/20/Rmnc57tIa2FfTCQ.png)