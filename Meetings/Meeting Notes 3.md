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
![[Pasted image 20240313132847.png]]
### - Spent time setting up and experimenting with Gazebo
```
cd Documents/Gazebo_Test/Sensor_tutorial/
ign gazebo sensor_tutorial.sdf
```
![[Pasted image 20240313133038.png]]
-Ackerman model
```
ign gazebo ackerman_steering.sdf
ign topic -t "/model/vehicle_blue/cmd_vel" -m ignition.msgs.Twist -p "linear: {x: 0.5}, angular: {z: 0.1}"
```
![[Pasted image 20240313133743.png]]
- Started looking at state estimation and scan matching
- Deliverable today


# Plan for next week:
 - Study state estimation theory
 - Do some research in regards to where there a gaps in the industry (Such as the fast image processing for racing)
 - Maybe add a lidar to the model and look at nav2? (SLAM stuff since this relates to what I have to do)