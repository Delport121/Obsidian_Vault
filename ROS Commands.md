Ros commnands

ros2 pkg create
ros2 run package exe
ros2 node list
ros2 node info /node
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
