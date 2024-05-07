## Raceline definition
 - Optimal path around the racetrack
  ![[Pasted image 20240129085327.png|400]]

##### Path vs Tracjectory
- Path planning $[x,y]$
- Trajectory planning $[x,y,v]$ (Velocity added)

- More information can be added in both instances
## Obtaining track data

![[Pasted image 20240129090201.png]]
Global trajectory planner
		-  Plan optimal trajectory
		- Consideration of vehicle dynamic limits
	Does not:
		- High level navigation
		- React to dynamic environments (Local trajectory planner)

## Raceline optimisation

- Shortest path problem (Geometric QP)
- Minimum curvature problem (Geometric QP)
- Minimum time problem (Optimal control)

- Solution differ in computation time
- Solutions differ in vehicle dynamics depth modelling
- Vehicle dynamics are important
## Raceline optimisation: Minimum curvature

- Pathplanning (Geometric QP) + Velocity planning
- Advantages:
	- Few parameter required 
	- Fast calculation times
### Pathplanning (Geometric QP)
#### Optimization problem: Quadratic programming
 ![[Pasted image 20240129091902.png|400]]
#### Geometrical optimization: Idea
![[Pasted image 20240129092013.png]]
![[Pasted image 20240129092107.png]]
#### Curvature Continuous Cubic Splines
![[Pasted image 20240129092537.png]]
#### Setting up linear equation system
![[Pasted image 20240129092948.png]]
![[Pasted image 20240129093000.png]]
### Velocity profile planning
![[Pasted image 20240129093741.png]]G-G Diagram
![[Pasted image 20240129093945.png]]
### Forward-Backward solver
![[Pasted image 20240129094634.png]]![[Pasted image 20240129094651.png]]