#ROS
# Section 6 Client/Server

## Services
- A ROS2 Service is a client/server system
- Synchronous or asynchronous
- One message type for Request, One message type for Response
- A Service can only exist once, but can have many clients
```python
self.server = self.create_service(<Type>, <name>, <callback>)
```
- Remember to add in setup.py under console scripts
```python
"add_two_ints_server = my_py_pkg.add_two_ints_server:main",  
```
To test simple service:
```bash
ros2 service call /add_two_ints example_interfaces/srv/AddTwoInts "{a: 3, b: 4}"
```

## Debug services
```bash
ros2 service list
ros2 service type <service_name>
ros2 service list -t 
ros2 service find <type_name>
ros2 service show <type_name>.srv
ros2 service call <service_name> <service_type> <arguments>
ros2 node info /<Nodename>
ros2 interface show <service_type>
rqt graph
```
## Remap service at runtime (Example)
Terminal 1:
```bash
ros2 run my_py_pkg add_two_ints_server --ros-args -r add_two_ints:=new_name
```
Terminal 2:
```bash
ros2 run my_py_pkg add_two_ints_client --ros-args -r add_two_ints:=new_name
```

Code available on Udemy at this lecture

# Section 7: Custom ROS interfaces
## Starting
To start of a package must be created. The default creation is for C++ thus why some folder are removed for python. 
- You must be in the src directory of your ros workspace
In terminal 1:
```bash
ros2 pkg create my_robot_interfaces
rm -rf include/
rm -rf src/
mkdir msg
```
The go to vscode and add the following lines to the package.xml file in the msg folder. Add it below "ament_cmake"
```python
<build_depend>rosidl_default_generators</build_depend>
<exec_depend>rosidl_default_runtime</exec_depend>
<member_of_group>rosidl_interface_packages</member_of_group>
```
Then navigate to the CMakeLists.txt file. the following lines were removed:
```
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

  

if(BUILD_TESTING)
find_package(ament_lint_auto REQUIRED)
# the following line skips the linter which checks for copyrights
# comment the line when a copyright and license is added to all source files
set(ament_cmake_copyright_FOUND TRUE)
# the following line skips cpplint (only works in a git repo)
# comment the line when this package is in a git repo and when
# a copyright and license is added to all source files
set(ament_cmake_cpplint_FOUND TRUE)
ament_lint_auto_find_test_dependencies()

endif()
```
Then still in terminal 1:
	-Start with capital
	- Camel case
	- No underscores etc.
```bash
cd msg/
touch HardwareStatus.msg
```
The CMakeLists.txt file shold be modified to look like this:
```
cmake_minimum_required(VERSION 3.8)
project(my_robot_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)

rosidel_generate_interfaces(${PROJECT_NAME}
"msg/MyMessage.msg"
)

ament_export_dependencies(rosidl_default_runtime)
  
ament_package()
```
Then navigate to the workspace directory and build:
```
colcon build --packages-select my_robot_interfaces
```
## Using custom messages in nodes
The video go into some detail about dependencies and stuff
```bash
ros2 interface show my_robot_interfaces
```

## Debug
```bash
ros2 interface < >
ros2 interface list
```
# Section 8: Change node settings at runtime

Better to show with a test:
In terminal 1:
```bash
ros2 run my_py_pkg number_publisher --ros-args -p test123:=3
//------------------------------------------------------------
ros2 run my_py_pkg number_publisher --ros-args -p number_to_publish:=3 -p publish_frequency:=4.5
```
In terminal 2:
```bash
ros2 param get /number_publisher test123
```
# Section 9:Launch Files
Create bringup pkg in src:
```bash
ros2 pkg create my_robot_bringup
cd my_robot_bringup/
rm -rf include/
rm -rf src/
mkdir launch
```
Some stuff can then be removed in CMakeList.text and added for this. This is the part that is added:
```
install(DIRECTORY
launch
DESTINATION share/${PROJECT_NAME}
)
```
Back in terminal:
```bash
cd launch
touch number_app.launch.py
chmod +x number_app.launch.py
```
In launch.py:
```python
from launch import LaunchDescription
from launch_ros.actions import Node

def genrete_launch_description():
	ld = LaunchDescription()
	
	number_publisher_node = Node(
	package="my_py_pkg",
	executable="number_publisher",
	)
	
	number_counter_node = Node(
	package="my_py_pkg",
	executable="number_counter",
	)
	
	ld.add_action(number_publisher_node)
	ld.add_action(number_counter_node)
	
	return ld
```
Then in package.xml:
```
<exec_depend>my_py_pkg</exec_depend>
```
Then finally configure the launch file as in the examples:
# Section 9: Ros bag
In terminal 1, navigate to desired directory:
```bash
mkdir Robotics_bags
cd Robotics_bags/
ros2 bag record /number
```
For custom name:
```bash
ros2 bag record /number -o test
```
For info:
```bash
ros2 bag info test/
```
Play info on topic
```bash
ros2 bag play test
```
Record all:
```bash
ros2 bag record -a -o test3
```
