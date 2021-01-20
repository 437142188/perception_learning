# perception_learning

## 值得学习的感知资料:

- [Super Fast and Accurate 3D Object Detection based on 3D LiDAR Point Clouds](https://github.com/maudzung/SFA3D)
 
  输入:L

  database:kitti

  基于YOLOV4架构,将点云数据压缩到BEV,作为网络的输入,backbone使用resnet,最终的位置和分类信息使用heatmap来回归,是一个anchor free的架构.因为将z坐标进行了简单压缩,因此丢失了点云的高度信息,检测效果有一定局限性,不过好在速度比较快,简化后的网络能够在cpu达到10hz以上,不过cpu占用率过高

- [OpenPCDet](https://github.com/open-mmlab/OpenPCDet)

  输入:L

  database:kitti,NuScenes,Waymo

  一款由商汤科技研发的基于点云的目标检测通用框架,里面集成了point pillars,pv_rcnn等多种点云检测网络,可拓展性强,不过对环境依赖比较强,需要专用的pytorch和spconv版本,环境搭建比较麻烦.point pillars的效率在gpu下能保证100hz以上,pv_rcnn能达到10hz

- [Awesome-3D-Detectors](https://github.com/Hub-Tian/Awesome-3D-Detectors)

  该仓库经常会检索一些前沿的3D目标检测文章,对了解前沿技术很有帮助