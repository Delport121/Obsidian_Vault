Ros commnands

ros2 pkg create
When making changes to code in vs - It has to be compiled again
colcon build  --packages-select my_py_pkg

or you can set it up to change as you change it in vs:
colcon build  --packages-select my_py_pkg --symlik-install

To run two same named nodes:
ro2 run my_py_pkg py_node --ros0args -r __node:=test

Creating a node
touch 'Nodename'

Making the node executable
chmod +x 'Nodename.py'

# Nodes
```
ros2 run <package_name> <executable>
ros2 node list
ros node info <node_name>
```
# Topics
```
rqt_graph
ros2 topic list
ros2 topic list -t 
ros2 topic echo <topic_name>
ros2 topic info <topic_name>
ros2 interface show <msg_type>
ros2 topic pub <topic_name> <msg_type> '<args>'
ros2 topic hz <topic_name>
```
# Services
```
ros2 service list
ros2 service type <service_name>
ros2 service list -t 
ros2 service find <type_name>
ros2 service show <type_name>.srv
ros2 service call <service_name> <service_type> <arguments>
```
# Parameters
```
ros2 param list
ros2 param get <node_name> <parameter_name>
ros2 param get <node_name> <parameter_name> <value>
```

# Terminal shortcuts
```
Ctrl+Shift+O (Split Horisontal) 
Ctrl+Shift+E (Split vertically)
Ctrl+Shift+W (Close terminal)
```

# Install stuff
## Setup Ros2
Do stuff provided on website

You don't want to source for each terminal everytime, thus this command is placed in:
```
gedit ~/.bashrc`
```
The command:
``` 
source/opt/ros/foxy/setup.bash
```

## Install ros2 build tool
```
sudo apt install python3-colcon-common-extensions
```
You don't want to source for each terminal every time, thus this command is placed in:
```
gedit ~/.bashrc
```
The command:
```
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash
```
## Creating a workspace
Make a folder
```
mkdir <ros2_ws>
```
Then move in the folder directory and  make a src folder
```
mkir src
```
Then
```
colcon build
```
## Local source
Paste in gedit ~/.bashrc
```
~/ros2_ws/install/setup.bash
```
## Creating packages
Cd directory
```
ros2_ws/src
```
and 
```
ros2 pkg create <my_py_ppkg> --build-type ament_python --dependencies rclpy
```
open srccd in vs code

# Gazebo

## Install through ros
```
sudo apt-get install ros-${ROS_DISTRO}-ros-gz
```
(Replace ${} with ros distribution)
Just follow the tuts

```
ign launch sensor_launch.ign
```
## Spawn URDF
First create empty world
```
ign gazebo empty.sdf
```
Get list of available services
```
ign service -l
```
Where looking for this:
/world/empty/create
To load model file
```
ign service -s /world/empty/create --reqtype ignition.msgs.EntityFactory --reptype ignition.msgs.Boolean --timeout 1000 --req 'sdf_filename: "rrbot.urdf", name: "urdf_model"'
```

# Running Gazebo with ROS
### Launch Gazebo
