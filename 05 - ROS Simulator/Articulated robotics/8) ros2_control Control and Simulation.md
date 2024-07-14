#ROS
# Controller manager
- Links together hardware drivers and controllers
# Hardware interfaces
-  Command interfaces: Things we can control
- State interfaces: Things we can only monitor
```bash
ros2 contril list_hardware_interfaces
```
- The controller manager uses something called a resource manager which gather all the hardware interfaces for the controllers
- Interacting with the controller manager:
	1) Via ROs services
	2) Via ros2 control CLI tool
	3) Via specialised nodes and scripts
- ![[Pasted image 20240530225526.png]]
# Controllers
![[Pasted image 20240530225713.png]]
# Testing in simulation
First install the follwing dependencies:
```bash
sudo apt install ros-humble-ros2-control ros-humble-ros2-controllers ros-humble-gazebo-ros2-control
```

- When not using Gazebo, well need to run ros2 run controller_manager ros2_control_node
# Starting the controllers
In terminal 1: We can build and start the simulation as normal:
```bash
ros2 launch my_bot launch_sim.launch.py world:=./dev_ws/src/my_bot/worlds/obstacles.world
```
In terminal 2: Check with the following command
```bash
ros2 control list_hardware_interfaces
```
Once this is done we can start the control manager with:
	- Note that the commands are changed for humble
```bash
	ros2 run controller_manager spawner -h
	ros2 run controller_manager spawner diff_cont
	ros2 run controller_manager spawner joint_broad
```
The command velocity is know published on /diff_cont/cmd_vel_unstamped and not cmd_vel. Thus,  when we run teleop we need to remap the topic
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped
```

The following then have to be added to the launch_sim.py file. Note that the changes of humble also apply here:
```python
diff_drive_spawner = Node(
    package="controller_manager",
    executable="spawner.py",
    arguments=["diff_cont"],
)

joint_broad_spawner = Node(
    package="controller_manager",
    executable="spawner.py",
    arguments=["joint_broad"],
)

# Then at the bottom...

return LaunchDescription([
    rsp,
    gazebo,
    spawn_entity,
    # ... anything else you've added in here...
    diff_drive_spawner,
    joint_broad_spawner
])
```
