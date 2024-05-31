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
We can build and start the simulation as normal:
```bash
ros2 launch my_bot launch_sim.launch.py world:=./dev_ws/src/my_bot/worlds/obstacles.world
```
In terminal 2: Check with the following command
```bash
ros2 control list_hardware_interfaces
```
Once this is done we can start the control manager with a spawner script