```bash
ros2 run landmark_extract slam_toolbox_logger --ros-args -r __ns:=/a200_1057 -r /tf:=tf -r /tf_static:=tf_static
```
```bash
ros2 run tf2_tools view_frames --ros-args -r __ns:=/a200_1057 -r /tf:=tf -r /tf_static:=tf_static

```