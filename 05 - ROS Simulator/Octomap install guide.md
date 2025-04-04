# Install
1. Install the following packages
```bash
sudo apt-get install ros-humble-octomap ros-humble-octomap-mapping ros-humble-octomap-msgs ros-humble-octomap-ros ros-humble-octomap-rviz-plugins ros-humble-octomap-server
```
2. Go to workspace src
3. Clone repo
```bash
git clone https://github.com/Taeyoung96/OctoMap-ROS2.git
```
4. cd ..
5. Build package
```
colcon build --packages-select octomap_msgs octomap_ros
source install/setup.bash
```
6. Then build all packages
```bash
colcon build
source install/setup.bash
```
## Changing parameters
In the octomap_mapping.launch.xml
- input_cloud_topic
- resolution
- frame_id
- base_frame_id
# Run octomap
```bash
[ros2 launch octomap_server2 octomap_server_launch.py](<ros2 launch octomap_server octomap_mapping.launch.xml>)
```
# Save map
```bash
ros2 run nav2_map_server map_saver_cli -f ~/ros2_ws/src/ --ros-args --remap map:=/projected_map
```

# Website links
This one worked well for Nico with his drone, I got it working the first time but not after that. It would not build anymore and caused issues. I believe this issue is likely caused by the underlay packages (/opt/ros/humble/) and the overlay packages from the workspace(~/dev_ws/install/) causing conflicts. It mixes up the header files causing build and dependency issues.
https://github.com/iKrishneel/octomap_server2

This repo seem to work and you can clone it directly in src. Follow the instructions. Do not worry that the packages are in a single octomap packages. The build commands still works as expected and it is nice and compact. 
https://github.com/Taeyoung96/OctoMap-ROS2

The official ros2 branch from octomap. This may be a nice way to go and perhaps the correct way
https://github.com/OctoMap/octomap_mapping

