# Graph based SLAM
## Idea of Graph-Based SLAM
- Use a <span style="color:rgb(255, 0, 0)"><span style="color:rgb(255, 0, 0)">graph</span></span> to represent the problem
- Every <span style="color:rgb(255, 192, 0)">node</span> in the graph corresponds to a pose of the robot during mapping
- Every <span style="color:rgb(255, 255, 0)">e<span style="color:rgb(255, 255, 0)">dg</span>e</span> between two nodes corresponds to a spatial constraint between them
- <span style="color:rgb(0, 176, 80)">Graph-based SLAM</span>: Build a graph and find a node configuration that minimize the error introduced by the constraints
## Summary
![[Pasted image 20240612174254.png]]
-  Graph based SLAM is sensor agnostic (Only requires two types of sensors)
	- One that can measure relative transformations between poses (IMU, odometry, wheel encoders). Used to build constraints between nodes
	- One that can measure absolute observation (Lidar,cameras) These sensor are used for loop closure
# Definition of the SLAM problem
![[Pasted image 20240612180559.png]]
## Probabilistic representation
![[Pasted image 20240612180728.png]]
![[Pasted image 20240612201335.png]]
### Motion model
![[Pasted image 20240612201616.png]]
### Observation model
![[Pasted image 20240612201644.png]]

- Check final notes as it appears to give some info regarding the MSE approach in graph SLAM, but it is unstructured