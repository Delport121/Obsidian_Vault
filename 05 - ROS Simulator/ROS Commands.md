#ROS
To run two same named nodes:


# Nodes
```bash
ros2 run <package_name> <executable>
ros2 node list
ros node info <node_name>
ros2 run <package> <node> --ros0args -r __node:=<nodename?>```
# Topics
```bash
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
```bash
ros2 service list
ros2 service type <service_name>
ros2 service list -t 
ros2 service find <type_name>
ros2 service show <type_name>.srv
ros2 service call <service_name> <service_type> <arguments>
```
# Parameters
```bash
ros2 param list
ros2 param get <node_name> <parameter_name>
ros2 param get <node_name> <parameter_name> <value>
```

# Terminal shortcuts
```
Ctrl+Shift+O (Split Horisontal) 
Ctrl+Shift+E (Split vertically)
Ctrl+Shift+W (Close terminal)
Shift+tab (Reverse tab)
```
# Terminal commands
```bash
pwd  (Get working directory)
```

# VsCode shortcuts
```
Command Palette (Ctrl+Shift+P)
auto format python (Ctrl+Shift+I)

Fold all (Ctrl + K, Ctrl + 0)
Unfold all (Ctrl + K, Ctrl + J)

See shortcuts (Ctrl + K, Ctrl + S)
```

# Install Ros notes
#### Setup Ros2
Do stuff provided on website

You don't want to source for each terminal everytime, thus this command is placed in:
```bash
gedit ~/.bashrc`
```
This open the folder in terminal, but you can add manually to the folder using
```bash
gedit ~/.bashrc
```
The command:
``` bash
source/opt/ros/foxy/setup.bash
```
#### Configuring environment
```bash
echo "export ROS_LOCALHOST_ONLY=1" >> ~/.bashrc
```
This command is the as adding the line below to the bashrc folder (Similar to what is done in Setup Ros2)
```bash
export ROS_LOCALHOST_ONLY=1
```
This ensures that our nodes are not published to eachother in the ESL

#### Install ros2 build tool
```bash
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

#### Creating a workspace
Make a folder
```bash
mkdir <ros2_ws>
```
Then move in the folder directory and  make a src folder
```bash
cd <ros2_ws>/
mkdir src
```
Then build the workspace (Must be in workspace directory )
Symlink install allows you to update code in vsCode without having to constantly rebuild
```bash
colcon build --symlink-install
```
## Local source
Paste in gedit ~/.bashrc
```bash
~/ros2_ws/install/setup.bash
```
## Creating packages
For when first creating in ros
```bash
cd ros2_ws/src
ros2 pkg create <my_py_ppkg> --build-type ament_python --dependencies rclpy
code .
```
## Building packages
```bash
colcon build  --packages-select my_py_pkg
```
or you can set it up to change as you change it in vs:
```bash
colcon build  --packages-select my_py_pkg --symlink-install
```

## Creating a node
Must be within node directory
Must add .py to name
```bash
touch <Nodename.py>
```
Making the node executable
```bash
chmod +x <Nodename.py>
```

## Launch command format
```bash
ros2 launch <package_name> <launch_file_name>
```
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
```bash
ign service -s /world/empty/create --reqtype ignition.msgs.EntityFactory --reptype ignition.msgs.Boolean --timeout 1000 --req 'sdf_filename: "rrbot.urdf", name: "urdf_model"'
```

# Running Gazebo with ROS
### Launch Gazebo

shift+tab+[]




Things in brandon's note that was that I added
- Create new folder with touch and make it an executable (Creating nodes)
- Colcon build in workspace
- Open src folder in vs code


