#ROS #SLAM
# Ros and SLAM
![[Pasted image 20240605161929.png]]![[Pasted image 20240605161952.png]]
![[Pasted image 20240605162049.png]]
Some SLAM system also want a base footprint frame. Its like a shadow of the base link on the horizontal plane for mapping in 3D

Pose: Position and orientation (Equivalent
to transform frame)
# Setting up the SLAM toolbox and creating a map
Lets first add the base footprint to `robot_core.xacro`
```xacro
<!-- BASE_FOOTPRINT LINK -->

<joint name="base_footprint_joint" type="fixed">
    <parent link="base_link"/>
    <child link="base_footprint"/>
    <origin xyz="0 0 0" rpy="0 0 0"/>
</joint>

<link name="base_footprint">
</link>
```
Then install the slam toolbox with
```bash
sudo apt install ros-humble-slam-toolbox
```

Were using the online asynchronous mode
-  Online: Working on live data stream
-  Asynchronous: Always processes the most recent scan to avoid lagging
To set this we do the following:
```bash
cp /opt/ros/humble/share/slam_toolbox/config/mapper_params_online_async.yaml dev_ws/src/my_bot/config/
```
(You can press double tab after `params_` to see a list of all the options)

## Creating a map

For a full start: (I'm going to start and assume I'm working in the workspace, hence the directories in the commands might change slightly)
Terminal 1:
```bash
ros2 launch my_bot launch_sim.launch.py world:=./src/my_bot/worlds/obstacles.world
```
In terminal 2:
```bash
rviz2 -d src/my_bot/config/main.rviz
```
In terminal 3: (Once again, see the different commands in the slam toolbox)
```bash
ros2 launch slam_toolbox online_async_launch.py slam_params_file:=/home/ruan/dev_ws/src/my_bot/config/mapper_params_online_async.yaml use_sim_time:=true
```
- (note that params_file is changed to slam_params_file in humble)
In terminal 4: (If a controller is not available)
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped
```

- Then in rviz, add a topic for map
- Make map the fixed frame
- You can also change the view
- Drive around a bit
- Note how the map origin transform stays the same and how odom moves due to drift See transform names)
- When you return to the map origin you will be more or less in the same origin as in gazebo

You can use the plugins in rviz to save the map. Add the slam toolbox panel in rviz
	Save Map: Old format that maps used and used to pas the map into external systems if required (.yaml and .pgm)
	Serialise Map: Save to reuse with the Slam toolbox (.data and .posegraph)
This will then appear as 4 folders in the workspace.

### Saving the map differently
The following command may also be used (although this is from a different tutorial)
```bash
ros2 run nav2_map_server map_saver_cli -f dev_ws/my_map
```
This save is in my home directory.  The argument after f is apparently `path/file` (No extension)

- You might have to run it more than one to save successfully. Check the logs

## Localisation with the SLAM toolbox
In the `mapper_params_online_async.yaml` file make the following changes from:
```yaml
 # ROS Parameters
    odom_frame: odom
    map_frame: map
    base_frame: base_footprint
    scan_topic: /scan
    use_map_saver: true
    mode: mapping #localization

    # if you'd like to immediately start continuing a map at a given pose
    # or at the dock, but they are mutually exclusive, if pose is given
    # will use pose
    #map_file_name: test_steve
    # map_start_pose: [0.0, 0.0, 0.0]
    #map_start_at_dock: true
```
To
```yaml
# ROS Parameters
    odom_frame: odom
    map_frame: map
    base_frame: base_footprint
    scan_topic: /scan
    use_map_saver: true
    mode: localization #mapping 

    # if you'd like to immediately start continuing a map at a given pose
    # or at the dock, but they are mutually exclusive, if pose is given
    # will use pose
    map_file_name: /home/dev_ws/my_map_serial
    # map_start_pose: [0.0, 0.0, 0.0]
    map_start_at_dock: true
```

- After many struggles I just could not get the saved map file to load. I continued to another tutorial that helped me implement  slam and NAV2 (RoboticsBackEnd) and continued with the video
- The error eventually was a spelling mistake of async instead of asynch
# Localisation with AMCL
To enable the following
![[Pasted image 20240606172513.png]]
```bash
ros2 run nav2_map_server map_server --ros-args -p yaml_filename:=my_map_save.yaml -p use_sim_time:=true
```
We need to activate something else for this node as it will be waiting in limbo
```bash
ros2 run nav2_util lifecycle_bringup map_server
```
Then run the nav2_amcl
```bash
ros2 run nav2_amcl amcl --ros-args -p use_sim_time:=true
```
And activate it:
```bash

```



In default
```bash
ros2 launch slam_toolbox online_async_launch.py slam_params_file:=/home/ruan/dev_ws/src/my_bot/config/mapper_params_online_async.yaml use_sim_time:=true
```




```bash
killall gzserver
killall gzclient
```