# Colab_FasterRCNN_Pytorch
在Google云盘的Colab跑Faster-Rcnn pytorch版

该代码主要参考了jwyang/faster-rcnn.pytorch的PyTorch复现工程

**参考源码：**

faster-rcnn pytorch代码下载
* pytorch0.4.0版源码：[pytorch0.4.0版源码](https://github.com/jwyang/faster-rcnn.pytorch)
* pytorch1.0.0版源码：[pytorch1.0.0版源码](https://github.com/jwyang/faster-rcnn.pytorch/tree/pytorch-1.0)

**一定要下载对应pytorch版本的源码！不然运行版本不兼容**



### 【数据集】
**此次训练使用的是VOC 2007数据集**

1.下载压缩文件到data 
* wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtrainval_06-Nov-2007.tar
* wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtest_06-Nov-2007.tar
* wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCdevkit_08-Jun-2007.tar
* 注意：wget是一个下载工具，linux系统中会自带wget，Windows环境下需要下载，教程地址：[windows安装wget教程](https://jingyan.baidu.com/article/6b1823098e049aba58e15921.html)

2.解压数据到data/VOCdevkit
* tar xvf VOCtrainval_06-Nov-2007.tar
* tar xvf VOCtest_06-Nov-2007.tar
* tar xvf VOCdevkit_08-Jun-2007.tar

3.创建软链接
* cd faster-rcnn.pytorch/data
* ln -s VOCdevkit的绝对路径 VOCdevkit2007
* Tips：其实这步可以不执行，**直接将VOCdevkit文件名改成VOCdevkit2007**，PASCAL VOC 2010 and 2012、COCO等数据集也是如此操作。

* 若使用COCO数据集训练，可参考链接:[准备COCO数据集](https://blog.csdn.net/The_heart_of_robort/article/details/85224232?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522167532935416800186545650%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=167532935416800186545650&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~first_rank_ecpm_v1~times_rank-15-85224232-null-null.blog_rank_default&utm_term=win10%20faster%20rcnn%20pytorch0.4.0&spm=1018.2226.3001.4450)


### 【下载预训练模型】

* VGG16: [Dropbox](https://www.dropbox.com/s/s3brpk0bdq60nyb/vgg16_caffe.pth?dl=0), [VT Server](https://filebox.ece.vt.edu/~jw2yang/faster-rcnn/pretrained-base-models/vgg16_caffe.pth)

* ResNet101: [Dropbox](https://www.dropbox.com/s/iev3tkbz5wyyuz9/resnet101_caffe.pth?dl=0), [VT Server](https://filebox.ece.vt.edu/~jw2yang/faster-rcnn/pretrained-base-models/resnet101_caffe.pth)

下载相应的预训练权重，并放到data/pretrained_model文件夹下，从实验发现caffe得到的预训练权重模型精度更高，因此使用了caffe的预训练权重。

### 【测试】

本次colab中只包含到训练部分展示，测试可根据具体情况进行

训练完想要测试模型在测试集上的前向效果，运行如下指令：
```
python test_net.py --dataset pascal_voc --net vgg16 \
                   --checksession $SESSION --checkepoch $EPOCH --checkpoint $CHECKPOINT \
                   --cuda
```
SESSION、EPOCH、CHECKPOINT修改为自己想要前向测试的模型

操作步骤可参考链接：第8步骤[测试test_.net.py](https://blog.csdn.net/weixin_44398211/article/details/114229817?spm=1001.2101.3001.6650.14&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-14-114229817-blog-105264651.pc_relevant_aa&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-14-114229817-blog-105264651.pc_relevant_aa&utm_relevant_index=23)

### 【使用自己数据集】

若想要使用自己的数据集训练，可参考链接第三步[使用自己的数据集训练](https://blog.csdn.net/ThunderF/article/details/100294913?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522167531313616800215069318%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=167531313616800215069318&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~first_rank_ecpm_v1~rank_v31_ecpm-3-100294913-null-null.blog_rank_default&utm_term=windows%20%E7%BC%96%E8%AF%91faster-rcnn&spm=1018.2226.3001.4450)

### 参考链接

自编写详细教程：[百度网盘word教程](链接：https://pan.baidu.com/s/1HzZKz97s8YoZxNvosvpbZw?pwd=oubt 
提取码：oubt)

参考CSDN链接：
* Goolge Colab使用教程[Goolge Colab使用教程](https://blog.csdn.net/weixin_45912366/article/details/124253460?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522167539440816800192218631%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=167539440816800192218631&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-124253460-null-null.142^v72^pc_search_v2,201^v4^add_ask&utm_term=colab%E9%87%8D%E5%91%BD%E5%90%8D%E6%96%87%E4%BB%B6%E5%90%8D%E5%91%BD%E4%BB%A4&spm=1018.2226.3001.4187)
* Google colab 跑通 faster-rcnn_G果的博客-CSDN博客_resnet101_caffe.pth[Google colab 跑通 faster-rcnn](https://blog.csdn.net/weixin_42899627/article/details/109460850?ops_request_misc=%7B%22request_id%22%3A%22167534338916800182716603%22%2C%22scm%22%3A%2220140713.130102334.pc_all.%22%7D&request_id=167534338916800182716603&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-8-109460850-null-null.142%5Ev72%5Econtrol_1,201%5Ev4%5Eadd_ask&utm_term=colab%E5%AE%89%E8%A3%85scipy&spm=1018.2226.3001.4187)
* 【Google云盘的Colab跑Faster-Rcnn pytorch版】_m0_45318906的博客-CSDN博客[Google云盘的Colab跑Faster-Rcnn pytorch版](https://blog.csdn.net/m0_45318906/article/details/122561133?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522167534338916800182716603%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=167534338916800182716603&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-122561133-null-null.142^v72^control_1,201^v4^add_ask&utm_term=colab%E5%AE%89%E8%A3%85scipy&spm=1018.2226.3001.4187)
* Faster-RCNN.Pytorch的使用_ThunderF的博客-CSDN博客[Faster-RCNN.Pytorch的使用](https://blog.csdn.net/weixin_44398211/article/details/114229817?spm=1001.2101.3001.6650.14&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-14-114229817-blog-105264651.pc_relevant_aa&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-14-114229817-blog-105264651.pc_relevant_aa&utm_relevant_index=23)

参考视频：[Bilibili_Colab_faster_rcnn][使用google colab 训练Faster RCNN教程_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Ka4y1v74p/?spm_id_from=333.999.0.0&vd_source=7f4303ee47e890f85798ca22b3dd22d3)



