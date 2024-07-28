# Setting up the driver stack
[Setting up the diver stack](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/firmware/drive_workspace.html#doc-drive-workspace)
This link shows how to create a basic f1tenth stack for the car. It contains the basic configurations and files for the vesc, ackerman steering and other things that the car require to operate.

It does not appear to work out of the box for our car. You my run into an error trying to run `ros2 launch f1tenth_stack bringup_launch.py`:
### Error: `Urg` node crashes when running `bringup`
The default stack also launches the `urg` node which is the lidar's node when you run `bringup.launch.py`. It's best to remove the line that launches the node in `bringup_launch.py`. The orignal urg node does not run properly 

There is a `Urg_node2` directory that you can place in your workspace's `src` directory as an alternative to the original. You can get this from the original `f1tenth_ws` workspace's `src`
- Remember to build the workspace after adding the new files
- In order for this to work you must add the path to this package in the bashrc file. (`ctrl+f` with 'f1tenth_ws' in the bashrc file to see where and how this is done)
# Mapping an environment
The mapping procedure is supposed the be very simple and easy. However, the slamtoolbox that you would normally use simply do not work. (This is also the one thatF1tenth uses). The slam node crashes without any proper crash logs. Reinstalling, debugging etc have been tried but no progress. Thus slam_gmappin was used which is also a package that you can add in the `src` directory of workspace. This slam version is actually included in the slam_toolbox aswell. 

- Make sure the odometry of the car is tuned as this will affect mapping.

Start of by starting up the car as normal:
Terminal 1:
```bash
urg
```
Terminal 2:
```bash
bringup
```

Make sure to connect the controller before continueing as the slam algoriithm require the odoetry topic to operate The odometry topic only 
start publishing once this is done.

The you can run the slam algorithm:
Terminal 3:
```bash
ros2 launch slam_gmapping slam_gmapping.launch.py
```
(I made an alia for this command aswell called `slam2`)

You can view the map creation process in rviz:
Terminal 4:
```bash
rviz2
```

Now drive the car slowly and steadily to start mapping the environment. The more you drive the better the map will start shaping. 
- Try keeping your distance from the car when mapping. Even when walking behind it the lidar wil still detect you when it turns and this messes up the map. (I sat on the table in the workshop when doing this)
- Also the lidar mapping is more reliable with smooth surfaces, so try to remove things like chairs or with objects with wierd geometry if possible.

Once your satisfied with the map, save it with:
Terminal 5:
```bash
ros2 run nav2_map_server map_server_cli -f <My_map_name> 
```
(Add your desired map name in the brackets)

The command will save two a `.pgm` and `.yaml` file in the directory that you are currently with your mapname. 
# Map Post processing
The map while most like be noisy. Noisy segments (Such as black squares in spaces that should be open) can be edited out using Microsoft paint. Some people use Photoshop and there are many ways to do this. I you want to generate racelines or waypoints, you can also close of corridors and gaps with black pixels.

# Loading and localising on the new map
Localising on the new map also require the particle filter to be setup. Chris made a guide on this, but I just used the one that was already setup in `f1tenth_ws`. The directories referred to in this section is for `f1tent_ws`

Add the two map files to the following directory in your workspace:
`/src/particle_filter/maps`

Then in the `localize.yaml` file located in `/src/particle_filter/config`
change the `map` parameter under `map_server` to your maps name.

When you now startup the car and the particle filter, the selected map should appear in rviz


