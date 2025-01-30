# Create a C++ package
In workspace/src directory:
```bash
ros2 pkg create my_cpp_pkg --build-type ament_cmake --dependencies rclcpp
```
Build selected package
```bash
colcon build --packages-select my_cpp_pkg
```
# Make node
In workspace/src/cpp_package/src
```bash
touch my_first_node.cpp
```
### VScode might not know path
Set path
- ctrl+shift+P
- Go to C/C++: edit Configurations (JSON)
Make sure this directory is included in the list 
- "/opt/ros/humble/include/
You can also cd into this directory to see all the available packages
## Demo code
```cpp
#include "rclcpp/rclcpp.hpp"

int main(int argc, char * argv[])

{
	rclcpp::init(argc, argv);
	auto node = std::make_shared<rclcpp::Node>("cpp_test");
	RCLCPP_INFO(node->get_logger(), "Hello, world!");
	rclcpp::spin(node);
	rclcpp::shutdown();
	return 0;
}
```
Create a executable and add it to the lib by adding the following lines to the cmake file
```cpp
add_executable(cpp_node src/my_first_cpp_node.cpp)
ament_target_dependencies(cpp_node rclcpp)

install(TARGETS
	cpp_node
	DESTINATION lib/${PROJECT_NAME}

)
```
#  OOP Templates
Python
```python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
 
 
class MyCustomNode(Node): # MODIFY NAME
    def __init__(self):
        super().__init__("node_name") # MODIFY NAME
 
 
def main(args=None):
    rclpy.init(args=args)
    node = MyCustomNode() # MODIFY NAME
    rclpy.spin(node)
    rclpy.shutdown()
 
 
if __name__ == "__main__":
    main()

```
CPP
```cpp
1. #include "rclcpp/rclcpp.hpp"

3. class MyCustomNode : public rclcpp::Node // MODIFY NAME
4. {
5. public:
6. MyCustomNode() : Node("node_name") // MODIFY NAME
7. {
8. }

10. private:
11. };

13. int main(int argc, char **argv)
14. {
15. rclcpp::init(argc, argv);
16. auto node = std::make_shared<MyCustomNode>(); // MODIFY NAME
17. rclcpp::spin(node);
18. rclcpp::shutdown();
19. return 0;
20. }
```
ctrl+shift+I for indentation