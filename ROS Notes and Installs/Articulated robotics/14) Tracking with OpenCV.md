[https://articulatedrobotics.xyz/tutorials/mobile-robot/applications/objtrack]()
# Prework
## Install OpenCV
install openCV:
```bash
sudo apt install python3-opencv
```
## Fix twist_mux
Update the twist_mux file in the config b just adding the following code. The folder would now look like this:
```yaml
[ball_tracker:  
topic : cmd_vel_tracker  
timeout : 0.5  
priority: 20](<twist_mux:
  ros__parameters:
    topics:
      navigation:
        topic  : cmd_vel
        timeout  : 0.5
        priority: 10
      tracker:
        topic  : cmd_vel_tracker
        timeout  : 0.5
        priority: 20
      joystick:
        topic  : cmd_vel_joy
        timeout  : 0.5
        priority: 100>)
```
-  Make sure we remember to remap the output command velocity topic to match this name when it comes time.
## Preparing the simulation
Add a tennisball to gazebo simulation by adding a sphere. Change its colour to yellow for appearance and also change both the radius of the object and the collision to  0.033.
Also change the camera angle if needed by changing the z axis of the joint link in the camera.urdf

## Clone the ball tracker repo
Clone the following into the source directory:
```bash 
git clone https://github.com/joshnewans/ball_tracker.git
```
# Detecting the ball
This is the optical frame:
(The diameter is z)
![[Pasted image 20240624120601.png]]
## Running the node
```bash
ros2 run ball_tracker detect_ball --ros-args -p tuning_mode:=true -r image_in:=camera/image_raw
```
In rviz open a camera and image plugin. Tune the camera.
You can check the reading with the following:
```bash
ros2 topic echo /detected_ball
```
Once satisfied, write down the tuning params for later implementation.
# Advanced Tracking
the position of the ball will now be estimated with some very rough math. There are better ways to do this. 
![[Pasted image 20240624142050.png]]
In another terminal, run:
```bash
ros2 run ball_tracker detect_ball_3d
```
You can add a marker topic in rviz to visualise.
The nodes now looks like this:
![[Pasted image 20240624142109.png]]
# Following the ball
The you can also run:
```bash
ros2 run ball_tracker follow_ball --ros-args -r cmd_vel:=cmd_vel_tracker
```
# Launch file and params
Add another ymal file to the config directory
```yaml
detect_ball:
  ros__parameters:
    # tuning_mode: false # Could set this here but leave it off so it can be easily set by the launch script
    x_min: 0
    x_max: 100
    y_min: 0
    y_max: 100
    h_min: 0
    h_max: 180
    s_min: 0
    s_max: 255
    v_min: 0
    v_max: 255
    sz_min: 0
    sz_max: 100

detect_ball_3d:
  ros__parameters:
    h_fov: 1.089
    ball_radius: 0.033
    camera_frame: "camera_link_optical"

follow_ball:
  ros__parameters:
    rcv_timeout_secs: 1.0
    angular_chase_multiplier: 0.7
    forward_chase_speed: 0.1
    search_angular_speed: 0.5
    max_size_thresh: 0.1
    filter_value: 0.9

```

You can view the available arguments with:
```bash
ros2 launch ball_tracker ball_tracker.launch.py --show-args
```

So to replicate all the previous behaviour:
```bash
ros2 launch ball_tracker ball_tracker.launch.py params_file:=src/my_bot/config/ball_tracker_params_sim.yaml image_topic:=/camera/image_raw cmd_vel_topic:=/cmd_vel_tracker enable_3d_tracker:=true
```
## Simulation recap
So the full startup for the ball tracker now is:
(While in dev_ws)
Terminal 1:
```bash
ros2 launch my_bot launch_sim.launch.py world:=./src/my_bot/worlds/obstacles.world
```
Terminal 2:
```bash
rviz2 -d src/my_bot/config/main.rviz
```
Terminal 3:
```bash
ros2 launch ball_tracker ball_tracker.launch.py params_file:=src/my_bot/config/ball_tracker_params_sim.yaml image_topic:=/camera/image_raw cmd_vel_topic:=/cmd_vel_tracker enable_3d_tracker:=true
```
