# Volta Arch

CUDA 9.0

warp矩阵函数(Warp-level Matrix Mulitply and Accumulate)



# GPU

![](https://i.bmp.ovh/imgs/2022/04/12/23cfa7dd1ec90d8d.png)

- Global Memory
- Streaming Multiprocessor (SM)
  - Include separate FP32 and INT32 cores


![image-20220412140021835](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220412140021835.png)

​		Tensor Core

![image-20220413094032577](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413094032577.png)

![image-20220413095447780](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413095447780.png)

![image-20220413095914553](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413095914553.png)



![image-20220413134058401](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413134058401.png)



Note：



![image-20220413152654889](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413152654889.png)

![image-20220413152518169](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413152518169.png)

![image-20220413153128881](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413153128881.png)

![image-20220413153322926](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413153322926.png)

![image-20220413153419687](C:\Users\sunq1\OneDrive - Intel Corporation\Documents\GitHub\ML-related\Notes\HPC\image-20220413153419687.png)

[ ERROR ]  Input 2 of node StatefulPartitionedCall/model/message_passing/edge_network/UnsortedSegmentSum was passed int64 from Stat

efulPartitionedCall/model/message_passing/edge_network/strided_slice_2_port_0_ie_placeholder:0 incompatible with expected int32
