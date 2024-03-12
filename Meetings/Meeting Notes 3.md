# Questions
- Re-explain low level features again, I think I had a different view of low level features
# What have I done:
#### - Got F1tenth simulator running
```
ros2 launch f1tenth_gym_ros gym_bridge_launch.py
```
```
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```
### - Spent time setting up and experimenting with Gazebo
```
cd Documents/Gazebo_Test/Sensor_tutorial/
ign gazebo sensor_tutorial.sdf
```
-Ackerman model
```
ign gazebo ackerman_steering.sdf
ign topic -t "/model/vehicle_blue/cmd_vel" -m ignition.msgs.Twist -p "linear: {x: 0.5}, angular: {z: 0.1}"
```
# Plan for next week:
 - Study state estimation theory
 - Do some research in regards to where there a gaps in the industry (Such as the fast image processing for racing)