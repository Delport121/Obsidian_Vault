#ROS #Purepursuit
In terminal in sim_ws directory:
`ruan@ruan-OptiPlex-7050:~/sim_ws$` 
```bash
ros2 launch f1tenth_gym_ros gym_bridge_launch.py
```
In another terminal directory:
`ruan@ruan-OptiPlex-7050:~/Ros2PP/src/my_waypoint_follower/my_waypoint_follower$`
```bash

```

# Setup
Change the mapname_list index variable in python file in directory to the desired map:
```bash
Ros2PP/src/my_waypoint_follower/my_waypoint_follower
```
Make sure that this map and its data is copied in directory
```bash
Home/sim_ws/src/f1tenth_gym_ros/maps
```
Change the map path in the sim.yaml file to the desired map. The file is located in 
```bash
Home/sim_ws/src/f1tenth_gym_ros/config
```

- Dont forget to source the two workspaces in the bash file.
