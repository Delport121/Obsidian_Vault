#SLAM #Scan_matching #Iterative_closest_point #Localization #Lectures
# 1 Localization with odometry
### Pose correction
![[Pasted image 20240313111906.png]]
- A fast scan rate is required
- Non smooth surfaces work better, smooth surfaces all look the same to the algorithm
# 2 Localization with scan matching
# 3 Iterative closest point algorithm
![[Pasted image 20240313115622.png|]]
![[Pasted image 20240612205858.png]]
![[Pasted image 20240313121230.png]]
A naive way to do this is to use the squared sum of distances
## ICP Assumptions and Limitations
- Assume sufficiently fast scan rate
	- Significant overlap will exist between most points
	- Points with high correspondence will exist
	- Assumes surface will be non-smooth and heterogeneous
	- A Smooth surface will look the same to the algorithm
- Practical limitations
	- initial guess is important for ICP to converge
	- Vinilla ICP can be slow
# 4 Iterative Closest point-to-line algorithm
Main improvements:
 - Point-to-point -> Point-to-line metric
 - Clever tricks in correspondence search
## Point-to-line metric
![[Pasted image 20240612223851.png]]
## Why is it faster
![[Pasted image 20240612224233.png]]
![[Pasted image 20240612224319.png]]
### Point-to-point metric
![[Pasted image 20240612224706.png]]
### Point-to-line metric
![[Pasted image 20240612224737.png]]
-The space of the transform is reduced -> Thus we have faster convergence
# Overall algorithm