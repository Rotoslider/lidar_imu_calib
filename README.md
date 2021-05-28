# lidar_imu_calib

### overview

when develop slam based on 3D lidar, we often use imu to provide priori for matching algorithm(icp, ndt), so the transform between lidar and imu need to be calibrated.For matching algorithm, attitude in transfom is more important than position in transform, and position often be set to 0. So this repo concentrate on calibrate attitude component in transform between lidar and imu.

### prerequisite 

- [ROS](http://wiki.ros.org/kinetic/Installation/Ubuntu)
### compile
```
  
cd catkin_ws/src
git clone https://github.com/Rotoslider/lidar_imu_calib.git
cd ..
catkin_make -DCATKIN_WHITELIST_PACKAGES="ndt_omp;lidar_imu_calib"
```
### run step

1. use rosbag tool record imu and lidar data

   ```
   rosbag record /imu /lidar_points
   ```

2. config launch file

   ```
   lidar_topic: lidar data topic name
   imu_topic: imu data topic name
   bag_file: *.bag file record imu and lidar data topic
   ```


3. start

   ```
   roslaunch lidar_imu_calib calib_exR_lidar2imu.launch
   ```
### reference
[https://blog.csdn.net/weixin_37835423/article/details/110672571](https://blog.csdn.net/weixin_37835423/article/details/110672571)
   
### troubleshooting
If you have issues with LZ4 streamDecode try running the lines below to fix the issue:

   ```
sudo mv /usr/include/flann/ext/lz4.h /usr/include/flann/ext/lz4.h.bak
sudo mv /usr/include/flann/ext/lz4hc.h /usr/include/flann/ext/lz4.h.bak

sudo ln -s /usr/include/lz4.h /usr/include/flann/ext/lz4.h
sudo ln -s /usr/include/lz4hc.h /usr/include/flann/ext/lz4hc.h

   ```
   
