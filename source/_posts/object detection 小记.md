title: 目标检测（图像篇）Object Detection(Image)
category: Object Detection
date: 2017-04-18
tags:
- Object Detection
- Deep Learning
- Computer Vision
lede: "论文要抓紧做了，加油加油！简单的一个小记录。paper放在这儿。物体（目标）检测历史发展，分析得十分到位，学习了！"
featured: true
---
论文要抓紧做了，加油加油！简单的一个小记录。

paper放在[这儿](https://github.com/StarsMyDestination/ML-Papers)

[物体（目标）检测历史发展](https://www.zhihu.com/collection/155393368)，分析得十分到位，学习了！

## Before Faster RCNN and YOLO
classic cv：HOG（方向梯度直方图）／ LBP（局部二值模式）+ sliding window（滑窗）／selective search（显著特征搜索） + SVM（ + AdaBoost）
>人工提取特征，一般要求你对机器图像领域有较为深刻的理解，另一个是运行速率慢。
<!-- more -->

rcnn 和 fast rcnn：selective search（显著特征搜索）=> region proposals（候选区域） + CNN判断物体是什么，优化框的位置  

>selective search 较为花费时间，而且圈出的候选区域假正例太多。

## Faster RCNN
省去了selective search，用rpn（region proposal network）替代，性能较rcnn和fast rcnn有较大提升。

Faster RCNN = RPN + Fast-RCNN， RPN负责寻找proposal，Fast-RCNN负责对RPN的结果进一步优化。其实RPN已经可以找到图片中每个物体的种类和位置，如果更注重速度而不是精度的话完全可以只使用RPN。

RPN是一个全卷积网络(FCN)，由于没有全连接层，所以可以输入任意分辨率的图像，经过网络后就得到一个feature map。这里要先介绍一下文章中提到的anchor这个概念，把这个feature map上的每一个点映射回原图，得到这些点的坐标，然后着这些点周围取一些提前设定好的区域，如选取每个点周围5x5的一个区域，这些选好的区域可以用来训练RPN。假设我们对feature map上的每个点选取了K个anchor，feature map的大小为H\*W\*C，那么我们再对这个feature map做两次卷积操作，输出分别是H\*W\*num_class\*K和H\*W\*4*K，分别对应每个点每个anchor属于每一类的概率以及它所对应的物体的坐标，那么怎么训练这个网络那？这个网络的loss function就是一个用于分类的softmax loss和一个用于回归的smooth L1 loss，输出对应的ground truth也很好得到，对于每个anchor，如果它和图片中某个物体的IOU(面积的交/面积的并)大于一个阈值，就认为它属于这一类，否则认为是背景，对于那些是背景的anchor回归的loss就是0，其他anchor位置的ground truth就是它们所对应的物体的位置。RPN其实也很简单，关键的地方就在于选取了一些anchor然后进行pixel-wise的学习。

RPN也有缺点，最大的问题就是对小物体检测效果很差，假设输入为512\*512，经过网络后得到的feature map是32\*32，那么feature map上的一个点就要负责周围至少是16*16的一个区域的特征表达，那对于在原图上很小的物体它的特征就难以得到充分的表示，因此检测效果比较差。


## YOLO 和 SSD
去掉了费时的RPN，输入任意大小的图片，输出目标位置和类别，即所谓端到端模型。
YOLO将图片resize到固定大小，划定固定数量的格子，若物体中心落在某个格子，则计算这个格子几个先验边框的分数和分类置信度。YOLO对同一个格子里的物体只能检测出一个，所以一些“小个子”就发现不了了。具体参见知乎大神2[YOLO](https://zhuanlan.zhihu.com/p/25045711)，[YOLO升级版](https://zhuanlan.zhihu.com/p/25052190)
SSD和YOLO很像，但是划分的格子有两种大小，一定程度上增加了小物体被检测到的几率。另外SSD借鉴了Faster-RCNN中Anchor Box的特点，用来框定目标位置，**在训练时ground truth会赋予给某个固定的Box。**另外，SSD采用了多尺度特征映射层，这也是其准确度再次提升的关键。[论文](https://arxiv.org/abs/1512.02325),github [caffe](https://github.com/weiliu89/caffe/tree/ssd) [tensorflow](https://github.com/balancap/SSD-Tensorflow)。TensorFlow源码分析参见知乎大神2的[这个博客](https://zhuanlan.zhihu.com/p/25100992)



## ref
http://lufo.me/2016/10/detection/

知乎大神1[目标检测算法历史发展](https://www.zhihu.com/collection/155393368)

知乎大神2[YOLO](https://zhuanlan.zhihu.com/p/25045711)，[YOLO升级版](https://zhuanlan.zhihu.com/p/25052190)

还是知乎大神2[SSD关键源码解析](https://zhuanlan.zhihu.com/p/25100992)

