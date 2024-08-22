#Scan_matching
### Problem statement
Given a scan and a map, or a scan and a scan, or a map and a map, find the rigid-body
transformation (translation+rotation) that aligns them best
### How scan matching works
With [[scan matching]] technology, measurements from the vehicle’s laser scanners are compared (matched) to the cells of a grid-based reference map of the environment. These cells can be compared to pixels in a digital image.

To position (localize) itself in the map, the navigation system calculates the vehicle’s position using the matched points. At the same time, it uses odometry, which measures the vehicle’s change in position by computing its movement. In rare cases, a scan matching system will regularly update the reference map with what the vehicle has ‘seen’.
### Scan matching algorithms
[[Iterative Closest Point]] (ICP) and [[Normal Distribution Transformation]] (NDT) are popular scan-matching algorithms that are used for local scan matching. ICP aligns two frames of point clouds based on distance judgement, while NDT uses a Gaussian distribution to model point clouds.

# Where is it used
## Localisation
- **Pose Refinement**: In the context of localization, scan matching is used to refine the robot's estimated position and orientation (pose) within a known map. After a rough estimate of the pose is made (e.g., using odometry or a motion model), scan matching compares the current sensor scan (e.g., from lidar) with the map to correct small errors in the pose estimate.
- **Monte Carlo Localization (MCL)**: Within MCL, scan matching can be used to improve the weight assignment to particles. By aligning the sensor scan with the map, the algorithm can determine which particles represent more likely positions, helping to converge on the correct localization.
## SLAM
- **Mapping and Pose Estimation**: In SLAM, scan matching is crucial for both mapping the environment and localizing the robot simultaneously. As the robot moves, it collects sensor data (e.g., lidar scans) and uses scan matching to estimate its pose relative to the environment. This estimate is then used to update the map with new information.
- **Loop Closure Detection**: Scan matching plays a vital role in detecting loop closures in SLAM. When the robot revisits a previously mapped area, scan matching helps recognize that the current scan aligns well with a part of the map that was recorded earlier. This information is used to correct accumulated errors in both the map and the robot's pose estimate, leading to a more accurate map.
- **Graph-Based SLAM**: In graph-based SLAM approaches, scan matching is used to create constraints between nodes in the pose graph. Each node represents a pose of the robot, and edges between nodes represent relative transformations (computed via scan matching) between these poses. Optimizing this graph yields the best estimate of the map and the robot's trajectory.

![[Scan matching.png]]

# References
https://bluebotics.com/differences-natural-navigation-scan-feature/
https://ignitarium.com/3d-lidar-slam-scan-matching-explained/


