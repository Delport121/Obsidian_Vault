```bash
sudo apt install ros-humble-octomap ros-humble-octomap-msgs ros-humble-octomap-server

```
Go to workspace src
```
colcon build --symlink-install --packages-select octomap_server2
```
Change neccasarry configurations in package launch file

Run octomap
```bash
ros2 launch octomap_server2 octomap_server_launch.py
```


Website links
https://github.com/iKrishneel/octomap_server2