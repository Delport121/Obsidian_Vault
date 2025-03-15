https://www.youtube.com/watch?v=NNR9RUNz5Pg&ab_channel=robotmania

###  PCL issue
Has an issue with colcon build where pcl_conversions are not found. The file causing the issue where:
```bash
/home/ruan/lio_sam_gazebo_ros2/src/LIO-SAM-ros2/include/lio_sam/utility.hpp
```
And here is the error in question when building:
```bash
In file included from /home/ruan/lio_sam_gazebo_ros2/src/LIO-SAM-ros2/src/imuPreintegration.cpp:1: /home/ruan/lio_sam_gazebo_ros2/src/LIO-SAM-ros2/include/lio_sam/utility.hpp:35:10: fatal error: pcl_conversions/pcl_conversions.h: No such file or directory 35 | #include <pcl_conversions/pcl_conversions.h> | ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ compilation terminated. gmake[2]: *** [CMakeFiles/lio_sam_imuPreintegration.dir/build.make:76: CMakeFiles/lio_sam_imuPreintegration.dir/src/imuPreintegration.cpp.o] Error 1 gmake[1]: *** [CMakeFiles/Makefile2:656: CMakeFiles/lio_sam_imuPreintegration.dir/all] Error 2 gmake[1]: *** Waiting for unfinished jobs....
```
1) The file were located as follow:
```bash
ruan@ruan-OptiPlex-7050:~$ locate pcl_conversions.h /opt/ros/humble/include/pcl_conversions/pcl_conversions/pcl_conversions.h
```
1) And the include line in Utility.hpp where changed to:
```C++
//#include <pcl_conversions/pcl_conversions.h>
#include <pcl_conversions/pcl_conversions/pcl_conversions.h>
```

# Simulation run commands
Run simulation:
```bash
source lio_sam_gazebo_ros2/install/setup.bash
ros2 launch robot_gazebo robot_sim.launch.py
```
Run LIO-SAM
```bash
source lio_sam_gazebo_ros2/install/setup.bash
ros2 launch lio_sam run.launch.py
```