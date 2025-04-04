# [Octomap](https://octomap.github.io/)
3D mapping method based on octree [data structure](https://octomap.github.io/octomap/doc/namespaceoctomap.html). Though it's a separate library/project, [[ROS2 |ROS]] comparability is maintained via the [octomap_ros](https://docs.ros.org/en/api/octomap_ros/html/) package and the [msg api](http://docs.ros.org/en/noetic/api/octomap_msgs/html/index.html) for sending the structures over [[ROS2#Topics |topics]].
## Installation
Installation of [Octomap](https://github.com/OctoMap/octomap_mapping/tree/ros2) and its dependencies can be done for [[ROS2]] Humble on Ubuntu 22.04LTS with the following command:
```bash
sudo apt-get install ros-humble-octomap ros-humble-octomap-mapping ros-humble-octomap-msgs ros-humble-octomap-ros ros-humble-octomap-rviz-plugins ros-humble-octomap-server
```
### CMake
```
find_package(octomap REQUIRED)
find_package(octomap_msgs REQUIRED)
add_executable(My_executable_node src/my_file.cpp)
ament_target_dependencies(My_executable_node rclcpp my_other_dependancies octomap_msgs octomap)
```
### Package.xml
```
<build_depend>octomap</build_depend>
<exec_depend>octomap</exec_depend>
<depend>octomap_msgs</depend>
```
### C++
```
#include <octomap_msgs/srv/get_octomap.hpp>
#include <octomap_msgs/conversions.h>
#include <octomap/octomap.h>
#include <octomap/math/Vector3.h>
```
## Mapping
A [server tool](http://wiki.ros.org/octomap_server) is provided to interface [[ROS2]] with octomap functions. It reads a PointCloud2 and odometry topic and publishes a marker array for visualisation. The mapper can be launched via provided launch.xml or another launch.py with the server parameters within:

```bash
ros2 launch your_package my_octomap.launch.xml
```

Maps can be saved via the terminal CLI with\[[yt_tut](https://www.youtube.com/watch?v=dF2mlKJqkUg)]:
```bash
ros2 run octomap_server octomap_saver_node --ros-args -p octomap_path:=save_file_path #.ot or .bt file extension
```

Maps can be read and published from saved files with:
```bash
ros2 run octomap_server octomap_server_node --ros-args -p latch:=true -p frame_id:=odom -p use_sim_time:=true -p octomap_path:=save_file_path#.ot or .bt file extension
```
## Issues
There are two notable drawbacks of this octree implementation:
- Node depth is not accessible from the API (must be inferred from other methods)
- Ray-casting though discrete voxels causes surfaces viewed at a shallow or tangent angles (the floor, round pillars, etc) to disappear. This impacts reliability and dependent processes.