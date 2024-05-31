# Controller manager
- Links together hardware drivers and controllers
# Hardware interfaces
-  Command interfaces: Things we can control
- State interfaces: Things we can only monitor
```bash
ros2 contril list_hardware_interfaces
```
- The controller manager uses something called a resource manager which gather all the hardware interfaces for the controllers
- ![[Pasted image 20240530225526.png]]
# Controllers
![[Pasted image 20240530225713.png]]
