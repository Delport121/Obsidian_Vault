#ROS
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard

ros2 launch my_bot launch_sim.launch.py

rviz2 -d src/my_bot/config/main.rviz

ros2 launch slam_toolbox online_async_launch.py slam_params_file:=/home/ruan/dev_ws/src/my_bot/config/mapper_params_online_async.yaml use_sim_time:=true

ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped

ros2 launch nav2_bringup navigation_launch.py use_sim_time:=true

colcon build --symlink-install

ros2 run tf2_tools view_frames

cp -r /home/ruan/Documents/image2gazebo/aut2 ~/.gazebo/models/

ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py

cd ~/.gazebo/models


./create_world.sh 0.05 0.3 aut_stl aut.png
./create_world.sh 0.05 0.3 gbr_stl gbr.png
./create_world.sh 0.05 0.3 esp_stl esp.png
./create_world.sh 0.05 0.3 mco_stl mco.png


export GAZEBO_RESOURCE_PATH=$GAZEBO_RESOURCE_PATH:/home/ruan/dev_ws/src/my_bot/worlds

ros2 launch my_bot launch_sim.launch.py --show-args

chmod +x robot_pose_publisher.py

```

Verbose example?
```python 
from launch import LaunchDescription
from launch_ros.actions import Node
from launch.actions import ExecuteProcess
import os

def generate_launch_description():
    world_file = os.path.join(
        # Path to your .world file
        '/path/to/your/world', 'your_world_file.world'
    )

    return LaunchDescription([
        ExecuteProcess(
            cmd=['gazebo', '--verbose', world_file, '-s', 'libgazebo_ros_factory.so'],
            output='screen'
        ),
        # Other nodes go here
    ])

```
Transitioning map server:
```bash
ros2 lifecycle set /map_server configure
ros2 lifecycle set /map_server activate

```

