#ROS
https://articulatedrobotics.xyz/tutorials/mobile-robot/applications/adv-teleop
-  This has not been done in detail, just a general overview for future reference
# Streaming to a phone or tablet
# Foxglove
Useful tool similar to rviz, can apparently do a lot more with it than what is here currently

# Extra
## Teleop from RViz

## Stamped/Unstamped Twist
Twist with time and transform frame associated with it
![[Pasted image 20240605151853.png|400]]

- Usefull for when there are network delay. It prevents the robot from executing previous commands.
The website provides a good reference point for installing and implementing it
## Gazebo/Sim time
## Launch files
This was the only one I setup so far. It just add the controller nodes to `launch_sim.launch.py` so it does not have to be executed individually.
```python
joystick = IncludeLaunchDescription(
            PythonLaunchDescriptionSource([os.path.join(
                get_package_share_directory(package_name),'launch','joystick.launch.py'
            )]), launch_arguments={'use_sim_time': 'true'}.items()
)
```
Remember to add it in the launch description as well in `launch_sim.launch.py`
## New teleop_tools package
