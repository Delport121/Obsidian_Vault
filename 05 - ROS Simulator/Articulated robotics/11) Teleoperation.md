#ROS
https://articulatedrobotics.xyz/tutorials/mobile-robot/applications/teleop
# Connecting to the computer
Linux is wierd, so in order to get it to work we have to do the following:
Check if the game pad work :
```bash
sudo apt install joystick jstest-gtk evtest
```
One installed we can run it to check. Select the device number and see if it works:
```bash
evtest
```
also test with
```bash
jstest-gtk
```
# Connecting the gamepad to ros
We publish twist messages directly when using the keyboard. With the controller this process is split so we can use different controller etc.
![[Pasted image 20240605095019.png]]To see the devices:
```bash
ros2 run joy joy_enumerate_devices
```
Next do the following to see if it is working:
```bash
ros2 run joy joy_node # <-- Run in first terminal
ros2 topic echo /joy # <-- Run in second terminal
```
The tut provides and app the can be used to test the axis. I do not think it is really needed at this stage, but it is there.

It may also be interesting to check the param of the joystick with:
```bash
ros2 param list /joynode
```
# Creating a launch and params file
We’ll start with the launch file. Create `joystick.launch.py` in the launch directory, and copy-paste the launch script below. 
This script simply:
- Specifies the path to a params file
- Declares a joy node that uses the params file
- Launches it
```python
from launch import LaunchDescription
from launch_ros.actions import Node

import os
from ament_index_python.packages import get_package_share_directory

def generate_launch_description():

    joy_params = os.path.join(get_package_share_directory('articubot_one'),'config','joystick.yaml')

    joy_node = Node(
            package='joy',
            executable='joy_node',
            parameters=[joy_params],
         )

    return LaunchDescription([
        joy_node       
    ])
```
Then create a `joystick.yaml` file in the config directory and add the following:
```yaml
joy_node:
  ros__parameters:
    device_id: 0
    deadzone: 0.05
    autorepeat_rate: 20.0
```
We can then run the controller in ros with:
```bash
ros2 launch my_bot joystick.launch.py
```
# Converting joy to twist
We add the following in the `joystick.launch.py` 
```yaml
teleop_node = Node(  
package='teleop_twist_joy',  
executable='teleop_node',  
name = 'teleop_node',  
parameters=[joy_params],  
remappings=[('/cmd_vel', '/diff_cont/cmd_vel_unstamped')]  
)  
#...  
  
# And add to launch description at the bottom
return LaunchDescription([
	 joy_node,
	 teleop_node
])
```
Also add the following parameters to `joystick.launch.py`:
```yaml
# ... below the joy parameters

teleop_node:
  ros__parameters:
    
    axis_linear:  # Left thumb stick vertical
      x: 1
    scale_linear:
      x: 0.5
    scale_linear_turbo:
      x: 1.0

    axis_angular:  # Left thumb stick horizontal
      yaw: 0
    scale_angular:
      yaw: 0.5
    scale_angular_turbo:
      yaw: 1.0

    require_enable_button: true
    enable_button: 6  # Left shoulder button
    enable_turbo_button: 7  # Right shoulder button
```

You can then test the remote connection with the following:
Terminal 1"
```bash
ros2 launch my_bot joystick.launch.py
```
Terminal 2:
```bash
ros2 topic echo /diff_cont/cmd_vel_unstamped
```
# Driving the robot
Rviz look for a transform in order to function. Since I do not have a physical robot, I have to use gazebo.

# Getting Feedback
- Qos (Quility-of-service)
- Odometry
- Camera feed
- Lidar feed
- 
