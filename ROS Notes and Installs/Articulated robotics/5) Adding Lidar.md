# Lidars in Ros

## 2D Lidar and LaserScan
- Ros has a specific message type for 2D lidar: "sensor_msgs/LaserScan"
- It is basically an array pf floats with some additional data
- The laser scan message also tells us which TFframe the llidar is attached to
## 3D Lidar and PointCloud2
- The message type for 3D lidar is: "sensor_msgs/PointCloud2"

# Adding a laser frame to the URDF
Create new file in robot description and remember to add the line include line
```xml
... other includes in robot.urdf.xacro ...
<xacro:include filename="lidar.xacro" />
```
Add the following in the new file:
```xml
<?xml version="1.0"?>
<robot xmlns:xacro="http://www.ros.org/wiki/xacro" >

    <joint name="laser_joint" type="fixed">
        <parent link="chassis"/>
        <child link="laser_frame"/>
        <origin xyz="0.1 0 0.175" rpy="0 0 0"/>
    </joint>

    <link name="laser_frame">
        ...fill in here next...
    </link>
</robot>
```
Then in the link fill area and in the file (Check the comments):
```xml
...In the link tag from above...

<link name="laser_frame">
    <visual>
        <geometry>
            <cylinder radius="0.05" length="0.04"/>
        </geometry>
        <material name="red"/>
    </visual>
    <collision>
        <geometry>
            <cylinder radius="0.05" length="0.04"/>
        </geometry>
    </collision>
    <xacro:inertial_cylinder mass="0.1" length="0.04" radius="0.05">
        <origin xyz="0 0 0" rpy="0 0 0"/>
    </xacro:inertial_cylinder>
</link>

...Wherever your materials are specified. robot_core.xacro for me...
<material name="red">
    <color rgba="1 0 0 1"/>
</material>
```
For the colour to work remember to add:
```xml
<gazebo reference="laser_frame">
    <material>Gazebo/Red</material>

    ... About to put stuff here ...
</gazebo>
```

Once all of this has been done, the launch file may be run again with the world saved in the previous lesson. 
```bash
ros2 launch my_bot launch_sim.launch.py world:=./dev_ws/src/my_bot/worlds/obstacles.world
```

# Integrating the real lidar
The next part of the video provides some useful info regarding the implementation of the real lidar. Refer back to this when the time comes. Easy access is also achieved with a launch file