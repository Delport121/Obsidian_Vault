#ROS #Gazebo
- Gazebo uses sdf format witch is similar tot  URDF
- SDF describe the world aswell as the models in it
- Gazebo uses plugins to communicate to the outside such as with ros
- An example of how it is integrated with ros
 ![[Pasted image 20240523093307.png]]

# Run the simulation
With the file urdf example properly setup in a workspace(It must be in the src file of the workspace)
You cna run the following commands
in terminal 1:
```bash
ros2 launch urdf_example rsp_sim.launch.py world:=~/my_world.world
```
The my world parameter is not working correctly. It is probably saved in the wrong directory
in the second terminal 2:
```bash
rviz2
```
The model should then load into gazebo. The camera and the depth camera can also be accessed in rviz by adding a image and point cloud subscribed to the relevant topic.
# Issue
The model would spawn in rvizz but not in gazebo. This was due to another instance of gazebo running, however it does not appear in the task bar. This then causes an issue withe the spawn entity service were it is not detected. As such you have to manually search for the gazebo in the system:
Check if gazebo is starting manually to ensure it starts coorectly:
```bash
gazebo --verbose -s libgazebo_ros_init.so -s libgazebo_ros_factory.so
```
If not, check the processes with:
```bash
ps aux | grep gazebo
```
This should display something like this:
```bash
ruan      12345  0.1  1.2 123456 12345 ?        Ssl  14:25   0:01 /usr/bin/gzserver ...
ruan      12346  0.0  0.5 123456 12345 ?        Sl   14:25   0:00 /usr/bin/gzclient ...

```
You can then kill the instance with either of the following commands. The second one is used if the process is stubborn. Be aware that one of the processes might be for the grep itself.
```bash
kill 12345 12346
kill -9 12345 12346
```
Check again with the first command.

There is an alternative shorter command for this in the video

