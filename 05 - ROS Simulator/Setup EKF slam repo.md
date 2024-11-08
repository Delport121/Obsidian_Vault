# Setup workspace
Make a workspace with and src directory. 
Clone repo into source directory.
```bash
https://github.com/maxipalay/ekf-slam.git
```
Try building:
- May get error regarding catch2 version:
```bash
git clone https://github.com/catchorg/Catch2.git
cd Catch2
cmake -Bbuild -H. -DBUILD_TESTING=OFF
sudo cmake --build build/ --target install
```

- May get error with custom message packages:
- Try building individual packages:
```
colcon build --packages-select nuturtlebot_msgs

``` 
Some packages are missing, so add the following in the src directory:
```bash
git clone https://github.com/NU-MSR/nuturtlebot_msgs.git
git clone https://github.com/ngmor/catch_ros2.git
```
The catch2 can also be installed like this if you do not want to install it from source
```bash
apt install ros-${ROS_DISTRO}-catch-ros2
```

# Run test
```bash
ros2 launch nuslam nuslam.launch.py robot:=nusim
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

