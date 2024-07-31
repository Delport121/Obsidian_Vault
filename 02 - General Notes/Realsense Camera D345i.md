# Installation
[Installation guide](https://github.com/IntelRealSense/realsense-ros/tree/ros2-development)The guide provides info on jetson installations as well.
[Rviz example](https://www.youtube.com/watch?v=d7JaQvmrVFA&ab_channel=MouserElectronics)The following shows how to use it in rviz and serve as a additional guide aswell. The guide seem to be for ros1 but the rviz stays the same
[Jetson Installation](https://dev.intelrealsense.com/docs/nvidia-jetson-tx2-installation)
# Usage
The single node can be run with the following command:
```bash
ros2 run realsense2_camera realsense2_camera_node
# or, with parameters, for example - temporal and spatial filters are enabled:
ros2 run realsense2_camera realsense2_camera_node --ros-args -p enable_color:=false -p spatial_filter.enable:=true -p temporal_filter.enable:=true>)
```
Using the launch file
```bash
ros2 launch realsense2_camera rs_launch.py

ros2 launch realsense2_camera rs_launch.py depth_module.depth_profile:=1280x720x30 pointcloud.enable:=true
```
# Rviz
- Frame should be `camera_link`
- For the point cloud subscribe to the following topic: `/camera/camera/depth/color/points`
- You have to run this with the pointcloud enabled (See last launch command above)
# Built in viewer
```bash
realsense-viewer
```
