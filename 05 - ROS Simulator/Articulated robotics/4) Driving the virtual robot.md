#ROS
When using gazebo and starting notes, be sure to enable "use simtime"
This synchronises the clock
# Start without launch file
In terminal 1:  Launch robot_state_publisher with  sim time
```bash
cd dev_ws/
source install/setup.bash
ros2 launch my_bot rsp.launch.py use_sim_time:=true
```
(You can check if it worked with:)
```bash
ros2 param get /robot_state_publisher use_sim_time
```
In terminal 2: Launch gazebo with ros compatibility
```bash
ros2 launch gazebo_ros gazebo.launch.py
```
In terminal 3: Spawn the robot
```bash
ros2 run gazebo_ros spawn_entity.py -topic robot_description -entity robot_name
```
# Launch with the launch file
Down load the provided file on the video or the website:
```python
from launch import LaunchDescription
from launch.actions import IncludeLaunchDescription
from launch.launch_description_sources import PythonLaunchDescriptionSource

from launch_ros.actions import Node



def generate_launch_description():


    # Include the robot_state_publisher launch file, provided by our own package. Force sim time to be enabled
    # !!! MAKE SURE YOU SET THE PACKAGE NAME CORRECTLY !!!

    package_name='articubot_one' #<--- CHANGE ME

    rsp = IncludeLaunchDescription(
                PythonLaunchDescriptionSource([os.path.join(
                    get_package_share_directory(package_name),'launch','rsp.launch.py'
                )]), launch_arguments={'use_sim_time': 'true'}.items()
    )

    # Include the Gazebo launch file, provided by the gazebo_ros package
    gazebo = IncludeLaunchDescription(
                PythonLaunchDescriptionSource([os.path.join(
                    get_package_share_directory('gazebo_ros'), 'launch', 'gazebo.launch.py')]),
             )

    # Run the spawner node from the gazebo_ros package. The entity name doesn't really matter if you only have a single robot.
    spawn_entity = Node(package='gazebo_ros', executable='spawn_entity.py',
                        arguments=['-topic', 'robot_description',
                                   '-entity', 'my_bot'],
                        output='screen')



    # Launch them all!
    return LaunchDescription([
        rsp,
        gazebo,
        spawn_entity,
    ])
```
Remember to change the package name to your robot's name
Remember to build
You can launch it with:
```bash
ros2 launch my_bot launch_sim.launch.py
```
# Understanding the control of the robot
![[Pasted image 20240524224609.png]]
![[Pasted image 20240524224755.png]]
![[Pasted image 20240524224803.png]]
# Adding the control plugin
Add an additional xacro file in the description directory "gazebo_control.xacro"
Remmeber to add a line in the "robot_urdf.xacro" file so the new file will also be included
Add the following code in the new file:
```xml
<?xml version="1.0"?>
<robot xmlns:xacro="http://www.ros.org/wiki/xacro">

    <gazebo>
        <plugin name='diff_drive' filename='libgazebo_ros_diff_drive.so'>
    
    
            <!-- Wheel Information -->
            <left_joint>left_wheel_joint</left_joint>
            <right_joint>right_wheel_joint</right_joint>
            <wheel_separation>0.35</wheel_separation>
            <wheel_diameter>0.1</wheel_diameter>
    

            <!-- Limits -->
            <max_wheel_torque>200</max_wheel_torque>
            <max_wheel_acceleration>10.0</max_wheel_acceleration>
    

            <!-- Output -->
            <odometry_frame>odom</odometry_frame>
            <robot_base_frame>base_link</robot_base_frame>

            <publish_odom>true</publish_odom>
            <publish_odom_tf>true</publish_odom_tf>
            <publish_wheel_tf>true</publish_wheel_tf>
    
    
        </plugin>
    </gazebo>

</robot>
```

# Driving the robot
Start the robot in gazebo and control it with:
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

# Visualising in Rviz
You can visualise the robot and what it is seeing in rviz for gazebo. Once you have the desired config you can save it in the config directory in the src file of the workspace

# Making a obstacle course
Similarly, a world can be saved in gazebo and saved in the world folder in the src directory of the workspace
You can then load the world up directly with the following command:
```bash
ros2 launch my_bot launch_sim.launch.py world:=path/to/my.world
```
In my case:
```bash
ros2 launch my_bot launch_sim.launch.py world:=./dev_ws/src/my_bot/worlds/obstacles.world
```

# Troubleshooting
You can check the velocity input with:
```bash
ros2 topic echo /cmd_vel
```
