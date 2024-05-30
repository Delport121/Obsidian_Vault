```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard

ros2 launch my_bot launch_sim.launch.py world:=./dev_ws/src/my_bot/worlds/obstacles.world

rviz2

colcon build --symlink-install

```