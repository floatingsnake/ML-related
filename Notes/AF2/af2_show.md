AVX512

03 自动化去掉，不要分支预测，会变快。原因50 / 50

match = icelake-server



numactl

mpirun 自己的

np: number of process. 多少个instance

ppr: process per rank.

rank: node

core per socket: 一个节点两个cpu：一个node两个socket

8 ice-lake node



单个node 2.3TB 并行

instance增加，内存上升

scale out. 

mpirun 

**fold change** is linear, work

- MSA packege, old implimentation, AVX512

 - affient
  Numactl OpenMP

4 seqs

paraellel,  at home operation, each line.

64 seqs.



Pytorch:

​	1,made intel pytorch: CPU. 

​	2.easy to debug, in eger mode]

Op Profiler

fuse operation.

bottle neck is allocation.

Jemalloc:Open   malloc

​     自旋锁

​	 互斥锁



one DNN, intel opitimis focus on op, nn.moduels: pre-comple

torch.op: MKL  atom-op 矩阵运算

oneAPI: IPX

NHWC data 如何存储矩阵

NCHW data



ONNX real time

​	不需要的op

OpenVino

​	torch

JIT



10.238.151.27

apply to apply. 两者一一对应

