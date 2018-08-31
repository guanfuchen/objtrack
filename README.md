# objtrack

基于视频的目标跟踪算法研究

对相应的视频目标跟踪论文整理实现综述文档。

---
## 数据集

### Online Object Tracking: A Benchmark

- [Online Object Tracking: A Benchmark](https://www.cv-foundation.org/openaccess/content_cvpr_2013/papers/Wu_Online_Object_Tracking_2013_CVPR_paper.pdf)

### The Visual Object Tracking VOT2014 challenge results

...

### Long-term Tracking in the Wild: A Benchmark

主页[Long-term Tracking in the Wild: A Benchmark](https://oxuva.github.io/long-term-tracking-benchmark/) 代码[long-term-tracking-benchmark](https://github.com/oxuva/long-term-tracking-benchmark)

数据集包含366个序列，总共14小时的视频，比流行的OTB-100多26倍。

![](http://chenguanfuqq.gitee.io/tuquan2/img_2018_5/Screen_Shot_2018-07-15_08.10.45.png)

### MOT16

[MOT16](https://motchallenge.net/data/MOT16/)

```
XX /cygdrive/d/Data/MOT/train
$ tree -L 2
.
├── MOT16-02
│   ├── det
│   ├── gt
│   ├── img1
│   └── seqinfo.ini
├── MOT16-04
│   ├── det
│   ├── gt
│   ├── img1
│   └── seqinfo.ini
├── MOT16-05
│   ├── det
│   ├── gt
│   ├── img1
│   └── seqinfo.ini
├── MOT16-09
│   ├── det
│   ├── gt
│   ├── img1
│   └── seqinfo.ini
├── MOT16-10
│   ├── det
│   ├── gt
│   ├── img1
│   └── seqinfo.ini
├── MOT16-11
│   ├── det
│   ├── gt
│   ├── img1
│   └── seqinfo.ini
└── MOT16-13
    ├── det
    ├── gt
    ├── img1
    └── seqinfo.ini

28 directories, 7 files
```

```
.
├── MOT16-02
│   ├── det det.txt
│   ├── gt gt.txt
│   ├── img1 XX.jpg
│   └── seqinfo.ini
```

```
det.txt
每一行总共10
第一个表示第几帧，-1，X，Y，W，H，Score，-1，-1，-1
1,-1,1359.1,413.27,120.26,362.77,2.3092,-1,-1,-1
1,-1,571.03,402.13,104.56,315.68,1.5028,-1,-1,-1
1,-1,650.8,455.86,63.98,193.94,0.33276,-1,-1,-1
```

```
MOT16-06.npy
其中包含了appearance，前10个是det.txt格式的，表示这个appearance是哪一帧哪个bbox的appearance
detections.shape=(10853, 138)，所以appearance特征为138-10=128
```

```
seqinfo.ini
[Sequence]
name=MOT16-02
imDir=img1
frameRate=30
seqLength=600
imWidth=1920
imHeight=1080
imExt=.jpg
```

---
## 相关资料

- [siamese-fc](https://github.com/bertinetto/siamese-fc) [Fully-Convolutional Siamese Networks for Object Tracking](http://www.robots.ox.ac.uk/~luca/siamese-fc.html) 项目主页。
- Fully-Convolutional Siamese Networks for Object Tracking
- [Visual Tracking with fully Convolutional Networks](http://scott89.github.io/FCNT/) 本文主要结合了top layer（更加通用的目标检测）和lower layer（相似目标之间区分更大），实现了目标的定位跟踪，同时也说明了使用特征选择去除冗余的噪声feature map对于提升精度有较大的帮助。
- [open-vot](https://github.com/huanglianghua/open-vot) Python编写的开源视觉目标跟踪仓库。
- DCFNet: Discriminant Correlation Filters Network for Visual Tracking，相关代码[DCFNet_pytorch](https://github.com/foolwood/DCFNet_pytorch)
- Simple Online and Realtime Tracking with a Deep Association Metric

---
### Visual Tracking with fully Convolutional Networks

结合了top layer（更加通用的目标检测）和lower layer（相似目标之间区分更大），实现了目标的定位跟踪。

网络架构如下所示：

![](http://chenguanfuqq.gitee.io/tuquan2/img_2018_5/fcnt_pipeline.png)

---
### Learning Multi-Domain Convolutional Neural Networks for Visual Tracking

提出了多域表示学习和在线视觉跟踪，代码参考[MDNet matlab](https://github.com/HyeonseobNam/MDNet)和[py-MDNet](https://github.com/HyeonseobNam/py-MDNet)，运行该代码请在GPU上运行，网络参数大约为5.5G。

网络架构如下所示：

![](http://chenguanfuqq.gitee.io/tuquan2/img_2018_5/Screen_Shot_2018-07-12_09.30.09.png)

---

### Simple Online and Realtime Tracking with a Deep Association Metric

代码参考[deep_sort](https://github.com/nwojke/deep_sort)

基于原始框架，本文将大量的计算复杂度迁移到离线的预训练步骤，其中在这个步骤中学习了一种deep assocation metric。

帧间basis的数据关联。

尽管在跟踪精度和准确率上，SORT性能或得了较高的性能，但是SORT对于ID转换的频率较高。这是因为部署的关联评价指标仅仅在状态估计不确定性较低的前提下是精确的。本文通过用一个结合了运动和外形信息的信息评价指标来解决这个遮挡问题下的switches。

#### 参考资料

- [多目标跟踪方法：deep-sort](https://www.cnblogs.com/YiXiaoZhou/p/7074037.html)


---
## 目标跟踪

- [目标追踪之卡尔曼滤波](https://zhuanlan.zhihu.com/p/21692854)
