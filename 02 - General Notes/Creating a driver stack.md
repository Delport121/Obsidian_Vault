# Setting up the driver stack
[Setting up the diver stack](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/firmware/drive_workspace.html#doc-drive-workspace)

### Error: `Urg` node crashes when running `bringup`
The stack does not work as intended, you may run into an error with the urg node when running `bringup.launch.py` after just setting up the stack. It's best to remove the line that launches the node in the launch file and launch the node manually. There is a Urgnode2 package that you can place in the workspace's source file. Just make sure that when you do this you add the path to this package in the bashrc file.

# Mapping an environment
The mapping procedure is supposed the be very simple and easy. However, the slamtoolbox that you would normally use simply do not work. (This is also the one that the F1tenth uses). The slam node crashes without any proper crash logs. Reinstalling, debugging etc have been tried but no progress. Thus g_slam was used which is also a package that you can add in the `src` directory of workspace. This slam version is actually also included in the slam_toolbox. 

- Make sure the odometry of the car is tuned as this will affect mapping.

# Loading and localising on the new map
- Localising on the new map also require the particle filter to be setup

What is the difference between the slam toolbox and g_slam
