# perception_learning

## 值得学习的感知资料:

- [Super Fast and Accurate 3D Object Detection based on 3D LiDAR Point Clouds](https://github.com/maudzung/SFA3D)
 
  输入:L

  database:kitti

  基于YOLOV4架构,将点云数据压缩到BEV,作为网络的输入,backbone使用resnet,最终的位置和分类信息使用heatmap来回归,是一个anchor free的架构.因为将z坐标进行了简单压缩,因此丢失了点云的高度信息,检测效果有一定局限性,不过好在速度比较快,简化后的网络能够在cpu达到10hz以上,不过cpu占用率过高

- [OpenPCDet](https://github.com/open-mmlab/OpenPCDet)

  输入:L

  database:kitti,NuScenes,Waymo

  一款由商汤科技研发的基于点云的目标检测通用框架,里面集成了point pillars,pv_rcnn等多种点云检测网络,可拓展性强,不过对环境依赖比较强,需要专用的pytorch和spconv版本,目前成功的版本为ubuntu16.04+ python3.6.12+ cuda9.2+cudnn7.6.5+pytorch1.3.1+ spconv1.0, 环境搭建比较麻烦.point pillars的效率在gpu下能保证100hz以上,pv_rcnn能达到10hz

- [Awesome-3D-Detectors](https://github.com/Hub-Tian/Awesome-3D-Detectors)

  该仓库经常会检索一些前沿的3D目标检测文章,对了解前沿技术很有帮助

- [SMOKE](https://github.com/NMme/SMOKE)
  
  输入:I

  database:kitti

  出自纵目科技，经典的图像3d目标检测框架，网络结构近乎于端对端，没有什么花里胡哨，通过输入单目图像数据，直接学习3d信息

- [CaDDN](https://github.com/TRAILab/CaDDN)

  输入:I

  database:kitti

  效果不错的单目图像出3d信息的网络，基于pcdet框架编写，其中亮点在于单独学习了一个深度概率分布网络，用于提高深度估计的准确性，后面的目标检测网络与pointpillars相似

  ### tips:
    1. 基于之前安装的pcdet环境，由于pytorch是1.3.1版本，安装的kornia版本为0.1.4,并且修改了kornia/losses/focal.py文件，修改如下:
    ---
      weight = torch.pow(torch.tensor(1.) - input_soft,
                    self.gamma.to(input.dtype))
    修改为

      self.gamma = self.gamma.to(input.device)
      weight = torch.pow(torch.tensor(1.) - input_soft,
                          self.gamma.to(input.dtype))
    ---
    2. 由于电脑gpu只有8G内存，database中使用skimage.transform.resize函数对输入图像进行了resize(90,306）
    3. 网络中的ffe的backbone改成了ResNet50，预训练模型下载地址为https://download.pytorch.org/models/deeplabv3_resnet50_coco-cd0a2569.pth



