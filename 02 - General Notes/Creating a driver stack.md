# Setting up the driver stack for 
[Setting up the diver stack](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/firmware/drive_workspace.html#doc-drive-workspace)
This link shows how to create a basic f1tenth stack for the car. It contains the basic configurations and files for the vesc, ackerman steering and other things that the car require to operate.

It does not appear to work out of the box for our car. You my run into an error trying to run 
### Error: `Urg` node crashes when running `bringup`
The default stack also launches the `urg` node which is the lidar's node when you run `bringup.launch.py`. It's best to remove the line that launches the node in the launch file and launch the node manually. 

There is a Urgnode2 package that you can place in the workspace's source file as an alternative to the original. In order for this to work you must add the path to this package in the bashrc file. 
(`ctrl+f` with 'f1tenth_ws' in the bashrc file to see where this was done)
# Mapping an environment
The mapping procedure is supposed the be very simple and easy. However, the slamtoolbox that you would normally use simply do not work. (This is also the one that the F1tenth uses). The slam node crashes without any proper crash logs. Reinstalling, debugging etc have been tried but no progress. Thus g_slam was used which is also a package that you can add in the `src` directory of workspace. This slam version is actually also included in the slam_toolbox. 

- Make sure the odometry of the car is tuned as this will affect mapping.
# Map Post processing
The map while most like be noisy. Noisy segments (Such as black squares in spaces that should be open) can be edited out using Microsoft paint. Some people use Photoshop and there are many ways to do this. I you want to generate racelines or waypoints, you can also close of corridors and gaps with black pixels

# Loading and localising on the new map
- Localising on the new map also require the particle filter to be setup

What is the difference between the slam toolbox and g_slam
