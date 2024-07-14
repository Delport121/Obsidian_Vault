#ROS
https://articulatedrobotics.xyz/tutorials/mobile-robot/applications/ros2_control-extra/

# Gazebo Clock rate
Gazebo is set at a default of 10hz, in order to set this higher we can do the following:
We can make a `gazebo_paprams.yaml` file in config directory of our workspace and add the following in it:
```yaml
gazebo:  
	ros__parameters:  
		publish_rate: 400.0
```
The in the launch file we add the following line and update the gazebo plugin accordingly:
```python
# Include the Gazebo launch file, provided by the gazebo_ros package
    gazebo_params_path = os.path.join(
         get_package_share_directory(package_name),'config','gazebo_params.yaml')

    gazebo = IncludeLaunchDescription(
            PythonLaunchDescriptionSource([os.path.join(
                get_package_share_directory('gazebo_ros'), 'launch', 'gazebo.launch.py')]),
                launch_arguments={
                        'params_file': gazebo_params_path}.items()
         )
```

# Wheel drift
This issue is solved by changing the wheel geometry to spheres instead of cylinders. In effect the simulation is more "perfect" but it may not be desirable for real world application. Keep this in min for later simulations:
So basically for each wheel:
```xml
<geometry>
	<cylinder radius="0.05" length="0.04"/>
</geometry>
```
This must be changed to:
```xml
 <geometry>
            <sphere radius="0.05"/>
 </geometry>
```
# Swapping between control methods
This seems iffy, I will get back to it later

# Save Rviz config
Save the Rviz folder in the config directory of the workspace as `main.rviz`
It can then just be run with the following command. Note that the command will work depending on your current directory, so make sure your are in your workspace
```bash
rviz2 -d src/my_bot/config/main.rviz
```
or
```bash
rviz2 -d dev_ws/src/my_bot/config/main.rviz
```


# Control Ros from other parameters
DIY web server
foxglove studio
Rviz teleop
Stamped twists (Has time)