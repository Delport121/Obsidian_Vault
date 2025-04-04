The following ros packages should be installed for simulation purposes:
```bash
sudo apt install ros-humble-controller-manager
sudo apt install ros-humble-ros2-control
sudo apt install ros-humble-ros2-controllers
sudo apt install ros-humble-gazebo-ros2-control
sudo apt install ros-humble-gazebo-ros ros-humble-gazebo-ros-pkgs

```
Check for packages:
```bash
ros2 pkg list | grep controller_manager
```