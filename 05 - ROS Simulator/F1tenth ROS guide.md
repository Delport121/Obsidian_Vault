---
date: 2024-07-22T09:13
tags:
  - ROS
  - F1TENTH
---
Some notes on the various topics that you interface with when doing [ROS](https://stevengong.co/notes/Robot-Operating-System) development.

Command I use for first time launch

`cd ~/f1tenth_ws/src sudo rocker --nvidia --x11 --volume .:/sim_ws/src -- f1tenth_gym_ros`

For some reason, this command stopped working suddenly… so I have to use the version without gpu. `sudo docker-compose up`. Then, run the command

`docker exec -it f1tenth_gym_ros-sim-1 /bin/bash`

To change the sim.yaml,

`vim /sim_ws/install/f1tenth_gym_ros/share/f1tenth_gym_ros/config/sim.yaml`

Change to

`map_path: '/sim_ws/src/particle_filter/maps/e7_floor5_biggest'map_img_ext: '.pgm'`

Then, startup the simulator

`source /opt/ros/foxy/setup.bashsource install/local_setup.bashros2 launch f1tenth_gym_ros gym_bridge_launch.py`

You can run all of your ros2 stuff outside the container, my brain just short circuited.

`ros2 run rrt rrt —ros-args -p`

## Physical Car[](https://stevengong.co/notes/F1TENTH-ROS#physical-car)

#### Topics Published[](https://stevengong.co/notes/F1TENTH-ROS#topics-published)

On the physical car, the following ROS topics are automatically published:

- `/scan`: this topic maintains the `LaserScan` messages published by the LiDAR
- `/odom`: this topic maintains the `Odometry` messages published by the VESC
- `/sensors/imu/raw`: this topic maintains the `Imu` messages published by the VESC
- `/sensors/core`: this topic maintains the `VescStateStamped` messages published by the VESC on telemetry data

To drive the car autonomously, simply publish to the `/drive` topic and press the deadman’s switch (RB button on joystick):

- `/drive`: this topic is listened to by the VESC, needs `AckermannDriveStamped` messages. The `speed` and `steering_angle` fields in the `drive` field of these messages are used to command desired steering and velocity to the car.

## Simulation[](https://stevengong.co/notes/F1TENTH-ROS#simulation)

> Difference in Topic Names for Simulation <> Real
> 
> I didn’t know that simulation and physical car had different topic names.
> 
> The main difference is `/odom` vs `/ego_racecar/odom`. This is likely the reason that the simulation code was not working on the real car when you tried running the [Pure Pursuit Code](https://github.com/CL2-UWaterloo/f1tenth_ws/blob/main/nodes/pure_pursuit/src/pure_pursuit_node.cpp).

Also, it’s pretty cool how in simulation, you can have multiple cars.

In simulation, when you want to change the things, you need to

#### Topics Published[](https://stevengong.co/notes/F1TENTH-ROS#topics-published-1)

In **single** agent:

- `/scan`: The ego agent’s laser scan
- `/ego_racecar/odom`: The ego agent’s odometry
- `/map`: The map of the environment

A `tf` tree is also maintained.

In **two** agents (In addition to the topics available in the single agent scenario):

- `/opp_scan`: The opponent agent’s laser scan
- `/ego_racecar/opp_odom`: The opponent agent’s odometry for the ego agent’s planner
- `/opp_racecar/odom`: The opponent agents’ odometry
- `/opp_racecar/opp_odom`: The ego agent’s odometry for the opponent agent’s planner

#### Topics Subscribed[](https://stevengong.co/notes/F1TENTH-ROS#topics-subscribed)

In **single** agent:

- `/drive`: The ego agent’s drive command via `AckermannDriveStamped` messages
- `/initalpose`: This is the topic for resetting the ego’s pose via RViz’s 2D Pose Estimate tool. Do **NOT** publish directly to this topic unless you know what you’re doing.

TODO: kb teleop topics

In **two** agent (In addition to all topics in the single agent scenario):

- `/opp_drive`: The opponent agent’s drive command via `AckermannDriveStamped` messages
- `/goal_pose`: This is the topic for resetting the opponent agent’s pose via RViz’s 2D Goal Pose tool. Do **NOT** publish directly to this topic unless you know what you’re doing.