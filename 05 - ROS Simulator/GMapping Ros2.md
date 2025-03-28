# Installation
Clone the following repo into ros2 workspace/src
```bash
git clone https://github.com/Project-MANAS/slam_gmapping.git
```
This one may also be good
```bash
https://github.com/siddarth09/ros2_gmapping.git
```
When bilding the package may not be found. The name has to be changed form slam_gmapping to ros2_gmapping

It would seem that the launch file uses the wrong format when trying to run with
```bash
ros2 launch slam_gmapping slam_gmapping.launch.py
```
The contents of the launch file has to change from:
```python
from launch import LaunchDescription
from launch.substitutions import EnvironmentVariable
import launch.actions
import launch_ros.actions


def generate_launch_description():
    use_sim_time = launch.substitutions.LaunchConfiguration('use_sim_time', default='true')
    return LaunchDescription([
        launch_ros.actions.Node(
            package='slam_gmapping', node_executable='slam_gmapping', output='screen', parameters=[{'use_sim_time':use_sim_time}]),
    ])
```
To this:
```python
from launch import LaunchDescription
from launch.substitutions import LaunchConfiguration
import launch_ros.actions

def generate_launch_description():
    use_sim_time = LaunchConfiguration('use_sim_time', default='true')
    
    return LaunchDescription([
        launch_ros.actions.Node(
            package='slam_gmapping',
            executable='slam_gmapping',  # Fix: Use 'executable' instead of 'node_executable'
            output='screen',
            parameters=[{'use_sim_time': use_sim_time,
                'resolution': 0.3,  # Map resolution
                'maxRange': 20.0,     # Max range of the laser
                'minimumScore': 100,  # Score threshold for scan matching
                'linearUpdate': 0.5,  # Update map every 0.5 meters
                'angularUpdate': 0.1, # Update map every 0.1 radians
                'odomFrame': 'odom',  # Odometry frame
                'baseFrame': 'base_link',  # Base frame
                'mapFrame': 'map',    # Map frame
                'forceUpdateMap': True,  # Force update map on new scan
                'srr': 0.1,           # Scan-to-scan rotation error
                'str': 0.1,           # Scan-to-scan translation error
                'useScanMatcher': True  # Enable scan matching 
            }],
            remappings=[('/scan', '/scan')]  # Remap the LIDAR topic
        ),
    ])

```

## Changing parameters
The parameters can be changed in slam_gmapping.cpp, but you wil have to rebuilt each time you change. Changing values in the launch file did not seem to help, but this is probably since I used resolution instead of delta keyword.
- delta_ is the map resolution