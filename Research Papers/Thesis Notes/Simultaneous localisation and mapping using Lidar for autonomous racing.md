[[Simultaneous localisation and mapping using Lidar for autonomous racing.pdf]]

# 1) Introduction
## Previous developments
- EKF SLAM, Fast SLAM, Unscented Kalman
- Long range and low latency sensor are beneficial
	- Lidar and camera in a redundant system
	- Augmented by inertial sensors and odometer sensors
- Techniques that were use include
	- Lidar detects a region of interest and directs camera to that region to reduce computational complexity
	- Run a simplified steady state kalman filter while waiting for delayed measurements

# 2) System overwiew
- Provides a good diagram for their perception pipeline
# 3) Hardware
The selection of Lidar and the mounting thereof is explained

# 4) Environment perception
- ICP is dismissed as the setup makes this method unreliable
- Cone detection is explain and how the cones are identified using the lidar

# 5) SLAM
- Whole and many unreliable objects vs a spare map with spesific objects
- Online vs offlilne SLAM

- EKF vs FAST SLAM advantages and disadvantages
	- EKF better at closing long loops but takes longer to compute
	- Fast SLAM is better with ambiguous features and faster, thus making it more applicable to racing
## Controlled loop closure

# 6) Future work
- Some interesting suggestions are made in regards to sensor latency and fusion
- Kalman filter tuning
- Integrated cone detection
- Improved data association algorithm
- Deeper driver integration