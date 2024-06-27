# System Overview

# Mapping
- Uses hector SLAM
- Math is a bit wierd
![[Pasted image 20240612092124.png]]
## Parameters for Hector SLAM
![[Pasted image 20240612092209.png]]
# Particle filter Localization
## Localization with odometry
- Odometry = Open loop estimation = error increases over time
We use Monte Carlo localization
Alternate solutions: 
	- Kalman filter
	- Topological Markov localization (Uses histograms)
# AMCL
## Kullback-Leibler divergence (KLD Sampling)
- Cull redundent particles and improves performance
- Sample size is proportional to error between odometry position and odometry based approximation
## System transform tree
![[Pasted image 20240612110004.png]]
## Parameters
Input parameters
-  Laser scan
- Dead reckoning/odometry
- Map
Output parameters
- AMCL pose
- Particle cloud for debugging
# Recursive Bayes filter used in AMCL
Bayes filter
![[Pasted image 20240612114918.png]]
![[Pasted image 20240612115001.png]]
![[Pasted image 20240612115016.png]]
![[Pasted image 20240612115031.png]]
- Gaussian filter an it variant can only model Gaussian distributions
# Recursive bayes filtering using AMCL
![[Pasted image 20240612115235.png]]
![[Pasted image 20240612121254.png]]
![[Pasted image 20240612121303.png]]
## Particle filter algorithm
![[Pasted image 20240612121705.png]]
![[Pasted image 20240612121717.png]]
![[Pasted image 20240612121727.png]]
## Monte Carlo
![[Pasted image 20240612121912.png]]
![[Pasted image 20240612121924.png]]
# Particle filter tuning
![[Pasted image 20240612140006.png]]
![[Pasted image 20240612140024.png]]
![[Pasted image 20240612140034.png]]
![[Pasted image 20240612140047.png]]
![[Pasted image 20240612140055.png]]
![[Pasted image 20240612140106.png]] 