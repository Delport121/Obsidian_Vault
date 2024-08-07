#Scan_matching
### Problem statement
Given a scan and a map, or a scan and a scan, or a map and a map, find the rigid-body
transformation (translation+rotation) that aligns them best
### How scan matching works
With [[scan matching]] technology, measurements from the vehicle’s laser scanners are compared (matched) to the cells of a grid-based reference map of the environment. These cells can be compared to pixels in a digital image.

To position (localize) itself in the map, the navigation system calculates the vehicle’s position using the matched points. At the same time, it uses odometry, which measures the vehicle’s change in position by computing its movement. In rare cases, a scan matching system will regularly update the reference map with what the vehicle has ‘seen’.
### Scan matching algorithms
[[Iterative Closest Point]] (ICP) and [[Normal Distribution Transformation]] (NDT) are popular scan-matching algorithms that are used for local scan matching. ICP aligns two frames of point clouds based on distance judgement, while NDT uses a Gaussian distribution to model point clouds.
# References
https://bluebotics.com/differences-natural-navigation-scan-feature/
https://ignitarium.com/3d-lidar-slam-scan-matching-explained/


