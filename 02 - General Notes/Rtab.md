### RTAB Map 2
https://github.com/simonbogh/realsense-d435-rtab-map-in-ROS2/tree/main

Camera node:
```
ros2 launch realsense2_camera rs_launch.py align_depth.enable:=true pointcloud.enable:=true
```

Rviz2 (go find the config file as well)
```
rviz2
```

RTAB Map:
```
ros2 launch rtabmap_launch rtabmap.launch.py  args:="--delete_db_on_start"  depth_topic:=/camera/camera/aligned_depth_to_color/image_raw  rgb_topic:=/camera/camera/color/image_raw  camera_info_topic:=/camera/camera/color/camera_info  approx_sync:=false  frame_id:=camera_link
```

