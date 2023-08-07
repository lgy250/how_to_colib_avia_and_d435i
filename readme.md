### 该文档用于记录如何获取 livox avia雷达与 d435i相机的外参
    主要使用了mars实验室的项目，无须适用任何标定板
    https://github.com/hku-mars/livox_camera_calib

    过程参考了一篇文档：https://blog.csdn.net/qq_42751676/article/details/132065174
    其实按照官方的流程是一样的，这里面就是多一些自己要修改的内容
    按照文档中修改路径与相机的内参后，只需要将自己制作的data放入指定路径

### 如何将一个场景下多帧的雷达点云转化成一个pcd文件
    roslaunch livox_ros_driver livox_lidar_rviz.launch
#### 查看扫描点云与图像是否是合适的，特征多不多，能不能用于外参检测，如果合适就可以将点云录制下来，10秒左右就足够了
    rosbag record -a
#### 将bag中/livox/lidar话题中的点云转化为pcd文件
    rosrun pcl_ros bag_to_pcd 2023-08-07-14-30-59.bag /livox/lidar ./pcd_record
#### 转化完成之后会有很多很多帧的点云数据，建议使用cloudcompare进行合成
    关于cloudcompare的安装，ubuntu下非常简单
    sudo apt-get install snapd
    snap install cloudcompare
    cloudcompare.CloudCompare
#### 安装完成后直接将文件夹下的所有点云ctrl+a拉进界面，全选，Edit——Merge（合并）——Yes。导出时注意右下角可以选择格式，point cloud library 格式。



    