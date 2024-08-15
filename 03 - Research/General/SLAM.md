Simultaneous Localization and Mapping ([[SLAM]]) is a popular technique in robotics that involves building a map of an unknown environment while simultaneously localizing the robot within that environment. This process is crucial for autonomous robots to navigate and operate effectively in complex, unstructured environments. 

SLAM algorithms typically use sensors such as cameras, LiDARs, and/or odometry sensors to gather data about the environment and the robot’s motion. The gathered data is then processed to estimate the robot’s position and orientation in the environment, as well as to build a map of the environment. There is a variety of [[SLAM Types]]

The components of SLAM include the following: 

1. Sensor Data: LiDAR sensor data is used to measure distances to objects and generate 3D maps of the environment. 
2. Localization: The LiDAR SLAM algorithm estimates the robot’s pose (position and orientation) in real-time based on the LiDAR point cloud. 
3. Mapping: The point cloud generated from the LiDAR sensor is used to generate a map of the environment. 
4. [[Scan matching]]: The LiDAR SLAM algorithm uses scan matching to align consecutive LiDAR scans and estimate the robot’s pose. 
5. Feature Extraction: Salient features are identified from the LiDAR point cloud, which may include corners, line segments, or other geometric features. 
6. [[Feature Matching]]: The features from the current LiDAR scan are aligned with the features from the previous LiDAR scan to estimate the robot’s pose. 
# Navigation methods
If the reference (grid) map of a vehicle using scan matching navigation can be compared to a digital image made up of pixels, then the reference map of a feature matching vehicle is similar to a line drawing. This is seem to be more for visual slam though
![[SLAM.jpg]]
![[SLAM-1.jpg]]
# References
https://ignitarium.com/3d-lidar-slam-scan-matching-explained/