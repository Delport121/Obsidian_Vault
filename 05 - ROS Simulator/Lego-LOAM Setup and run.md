https://learnopencv.com/lidar-slam-with-ros2/
- Check at bottom of page for installation guide

# Installation
## Dependency management
### Install boost
```bash
# install boost
sudo apt install libboost-all-dev # experimented with version 1.74.0
```
### Install eigen
```bash
# remove eigen if you already have, sudo apt-get remove libeigen3-dev
wget https://gitlab.com/libeigen/eigen/-/archive/3.3.7/eigen-3.3.7.zip
unzip eigen-3.3.7.zip
cd eigen-3.3.7
mkdir build && cd build
cmake ..
sudo make install
```
### Install GTSAM
```bash
wget https://github.com/borglab/gtsam/archive/refs/tags/4.2.zip
unzip gtsam-4.2.zip
cd gtsam-4.2
mkdir build && cd build
cmake ..
sudo make install
```
- Note gtsam-4.2.zip might only save as 4.2.zip. Rename as necessary
### Clone LeGO-LOAM
```bash
git clone https//github.com/fishros/LeGO-LOAM-ROS2.git
```
- Note that the this link take you too the official Lego-LOAM github, and extract from this. The link in the readme for this repo seems to be slighly different to this. I could not get that to work though
### Cmake changes
Modify the CMakeLists.txt and LiDAR Topic Name:

This file needs to be modified for easy compilation of the LeGO-LOAM repository. This file can be found at `**LeGO-LOAM-ROS2/LeGO-LOAM/CMakeLists.txt**`. there are two modifications,

- `find_package(Eigen3 REQUIRED)` should be changed to `find_package(Eigen3 3.3.7 REQUIRED)`
- Add `include_directories(${EIGEN3_INCLUDE_DIR})` after `include_directories(include)`.

To modify the topic name find the file `imageProjection.cpp` and in the 46th line change `/rslidar_points` to `/velodyne_points`.

## Build
  ```bash
cd LeGO-LOAM-ROS2
colcon build
source install/setup.bash
```
  
## Convert example rosbag
Link to provided rosbag
https://drive.google.com/file/d/1s05tBQOLNEDDurlg48KiUWxCp-YqYyGH/view
Be in same directory as where bag is located
```bash
rosbags-convert --src nsh_indoor_outdoor.bag --dst nsh_indoor_outdoor_ros2
```

# Run
-  Remember to source 
```bash
# in a seperate terminal
ros2 launch lego_loam_sr run.launch.py
# in a seperate terminal
ros2 bag play nsh_indoor_outdoor
```