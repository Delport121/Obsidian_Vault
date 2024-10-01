#ROS
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard

ros2 launch my_bot launch_sim.launch.py world:=./dev_ws/src/my_bot/worlds/obstacles.world
#or
ros2 launch my_bot launch_sim.launch.py

rviz2 -d src/my_bot/config/main.rviz

ros2 launch slam_toolbox online_async_launch.py slam_params_file:=/home/ruan/dev_ws/src/my_bot/config/mapper_params_online_async.yaml use_sim_time:=true

ros2 launch nav2_bringup navigation_launch.py use_sim_time:=true

colcon build --symlink-install

```