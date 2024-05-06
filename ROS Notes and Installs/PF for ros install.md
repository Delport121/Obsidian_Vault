# 1. Clone PF repo
	make ros2 ws or cd into ros2 ws
```
cd src
git clone https://github.com/f1tenth/particle_filter.git
```

	change '-' to '_' in setup.cfg (should look like below):
```
[develop]
script_dir=$base/lib/particle_filter
[install]
install_scripts=$base/lib/particle_filter
```
	in terminal:
```
colcon build
```

```
# Do this at the root of your colcon workspace!!!!
sudo apt-get update
rosdep install -r --from-paths src --ignore-src --rosdistro humble -y
```

# 2. Download Rangelibc library
```
cd 
# No need to clone this in your workspace, we will only use the python wrapper
git clone https://github.com/f1tenth/range_libc
sudo apt-get install python3-dev cython3
cd range_libc/pywrapper
# on VM
./compile.sh
sudo TRACE=ON python3 setup.py install
```

# 3. Use Sim
To use it in the simulator, you must comment out the launch of the map_server in the launch file. In the launch/localize_launch.py ​​file, comment out these two lines (Towards the end of the file):
    ld.add_action(nav_lifecycle_node)
    ld.add_action(map_server_node)
Then, in the config/localize.yaml file, change the 'odometry_topic' to '/ego_racecar/odom' and 'range_method' to 'glt

```
colcon build
```

# 4. Usage
```
ros2 launch particle_filter localize_launch.py
```


# Fix to visualise fake scan

```python
def publish_scan(self, angles, ranges):

# publish the given angels and ranges as a laser scan message

ls = LaserScan()

ls.header.stamp = self.last_stamp

ls.header.frame_id = '/laser'

ls.angle_min = float(np.min(angles))

ls.angle_max = float(np.max(angles))

ls.angle_increment = float(np.abs(angles[0] - angles[1]))

ls.range_min = 0.0

ls.range_max = float(np.max(ranges))

# ls.ranges = ranges

ls.ranges = [float(range) for range in ranges]

self.pub_fake_scan.publish(ls)
```

# 5. Usage with Imings pure pursuit
In terminal 1:
```bash
ros2 launch f1tenth_gym_ros gym_bridge_launch.py
```
In terminal 2:
```bash
ros2 launch particle_filter localize_launch.py
```
In terminal 3:
Navigate to correct directory:
```bash
cd Ros2PP/src/my_waypoint_follower/my_waypoint_follower/
```
The run:
```bash
ros2 run my_waypoint_follower purePursuit_ros
```