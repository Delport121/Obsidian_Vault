#Motion_planning
# Getting started
## Installation
https://navigation.ros.org/getting_started/index.html#getting-started
1) 1. Install the [ROS 2 binary packages](https://docs.ros.org/en/rolling/Installation/Ubuntu-Install-Debians.html) as described in the official docs
2) Install the Nav2 packages using your operating system’s package manager:
```bash
sudo apt install ros-<ros2-distro>-navigation2
sudo apt install ros-<ros2-distro>-nav2-bringup
```
3) Install the Turtlebot 3 packages (Humble and older):
```bash
sudo apt install ros-<ros2-distro>-turtlebot3-gazebo
```
## Running the example
1) Start terminal in GUI
2) Set key environment variables
```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=waffle
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:/opt/ros/humble/share/turtlebot3_gazebo/models
```
3) In the same terminal, run:
```bash
ros2 launch nav2_bringup tb3_simulation_launch.py headless:=False
```
## Alternative start up
Each command in a differnet terminal. (will have 5 in total)
```bash
export TURTLEBOT3_MODEL=waffle
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py #Turtlebot

ros2 launch nav2_bringup navigation_launch.py use_sim_time:=True #Navigation2

ros2 launch slam_toolbox online_async_launch.py use_sim_time:=True #Slam toolbox

ros2 run rviz2 rviz2 -d /opt/ros/humble/share/nav2_bringup/rviz/nav2_default_view.rviz #rviz

export TURTLEBOT3_MODEL=waffle
ros2 run turtlebot3_teleop teleop_keyboard
```
## Save the map
(The previous 4 terminals must not be stopped)
```bash
ros2 run nav2_map_server map_saver_cli -f my_map
```
- You can provide an optional “-f” option to specify the path/name of the map. Make sure you don’t put any extension here, this will be done automatically.
- When you run the command, you’ll see some logs in white and yellow.
Now, you should have 2 new files:
- my_map.yaml: this file contains the metadata for the map, as well as the path to the image file.
- my_map.pgm: this is the image file with white, black and grey pixels, representing the free, occupied, and unknown space.