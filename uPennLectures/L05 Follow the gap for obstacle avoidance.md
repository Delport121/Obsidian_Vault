	Seek out the largest gap:
	Advantages:
		- Holonic robots and non0holonic robots in environment with  sparse obsticles
		Disadvantages
		- Doest account for safety
		- Doesnt consider car's dimensions
		- Hard to decide threshold t

##### FTG Tweak 1:
1) Find nearest Lidar point and put safety bubble $r_b$ around it
2) Set all points inside bubble to zero and the rest is free space 
3) Find the max length sequence among free space (max gap)
4) Find best point amongst maximum length sequence (Furthest point)

-) Changing speed results in losing velocity
![[Screenshot from 2024-01-24 16-45-13.png|200]]

##### FTG tweak 2 
1) Find disparities
2) Extend half the width for each disparity
3) Choose path based on virtual lidar readings
 ![[Screenshot from 2024-01-24 16-57-44.png|200]]
 
##### FTG tweak 3 
 Disparity extender - cornering
 1) Scan lidar samples -90 and +90 
 2) If any point is below a certain distance keep straight
 ![[Screenshot from 2024-01-24 17-07-38.png|200]]
 