The paper describes the design and implementation of an autonomous drone equipped with a special roll cage for mine exploration and mapping (GPS-denied environment)

### System Design
- Airframe
- Electronics
- Frame analysis:
	- CAD Simulation
	- Hydraulic press test

## Resilient autonomous exploration
A) Architecture: High level exploration planner

B) Perception: Lidar and IMU fusion

C) Path planning: Utilises a graph based path planner BPlanner2 (The software models the robot as a cuboid which poses problems in very narrow passages, however this remedied by exploiting the robot's collision tolerance and modelling the environment in the same resolution as the robot)

D) Control: Fixed gain PID scheme

E) Object detection and localisation
- Visual Detection: Uses a trained model to identify basic objects (YOLOv3)
- Localisation: The map is divided into a set of pixels 
- Detection and Bluetooth devices: Robot can detect active bluetooth devices
- Reporting: 



