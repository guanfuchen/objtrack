# objtrack

基于视频的目标跟踪算法研究

对相应的视频目标跟踪论文整理实现综述文档。

---
## 数据集

### Online Object Tracking: A Benchmark

- [Online Object Tracking: A Benchmark](https://www.cv-foundation.org/openaccess/content_cvpr_2013/papers/Wu_Online_Object_Tracking_2013_CVPR_paper.pdf)

### The Visual Object Tracking VOT2014 challenge results


---
## 相关资料

- [siamese-fc](https://github.com/bertinetto/siamese-fc) [Fully-Convolutional Siamese Networks for Object Tracking](http://www.robots.ox.ac.uk/~luca/siamese-fc.html) 项目主页。
- Fully-Convolutional Siamese Networks for Object Tracking
- [Visual Tracking with fully Convolutional Networks](http://scott89.github.io/FCNT/) 本文主要结合了top layer（更加通用的目标检测）和lower layer（相似目标之间区分更大），实现了目标的定位跟踪，同时也说明了使用特征选择去除冗余的噪声feature map对于提升精度有较大的帮助。


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