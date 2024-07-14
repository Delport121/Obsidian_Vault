#Local_planning #Motion_planning #Lectures
# The planning module
#### Mission/Global planner
- What is the overall goal of the vehicle?
#### Behavioural planner
- What rules should the vehicle follow in different situations?
#### Local planner
- What are the viable trajectories from position to goals?
![[The planning module.png]]
# Configuration space vs workspace

#### Configuration space:
A complete specification of the position of every point in the system
(All set of angles (theta 1 and 2) a two link arm can have)
#### Workspace:
The coordinates of the robot is specified in the same coordinate system as the the world it is manipulating
(All the areas the end-effect of a arm can be within space)
# Motion planning
![[Motion planning given.png]]
![[Motion planning goal.png]]
## Complete and Optimal motion planning
An algorithm is complete:
- Terminates in a finite time
- Returns a solution if one exists or a failure if one does not exist
An algorithm is optimal:
- Returns the minimum cost solution if it exists
# Probabilistic Road maps (PRM)
![[Probabilistic road map example.png]]
![[Pasted image 20240627140530.png]]
# Motion planning
- Discrete motion planning: Finite sequences of configurations (Motion is abrupt between a configuration and the next one)
- Continues motion planning: Continues paths
# Moving object planning (MOP)
![[Pasted image 20240627150408.png]]
- Tends to extends map where it already exists. Thus need to reduce sampling of already dense regions
# Rapidly-Exploring Random trees
![[Pasted image 20240627151657.png]]![[Pasted image 20240627151704.png]]
## Simple RRT Properties
- Rapidly explore open space
- All directions are explored evenly
- Inefficient at exploring promising directions
## Goal based RRT
 - Adds a bias that pick the goal to explore towards, allowing faster progress towards the goal
## Bidirectional RRT's
- Add bias to each tree towards nodes of the other tree
## RRT: Completeness and Optimality
- Probabilistically complete: 
	- The probability of returning a solution increases ad the number of random samples increases
- Not optimal
	- Due to random sampling
## RRT as a local planner
![[Pasted image 20240627153607.png]]
# Paths
## Splines
- Piece wise polynomials
- Different degrees of continuity
	![[Pasted image 20240627154038.png]]
- Types:
	- Cubis
	- Bezier
	- B-Splines
	- NURBS
## Curvature
![[L11 Local Planning - RRT Spline Base planning.png]]
# Clothoids
![[L11 Local Planning - RRT Spline Base planning-1.png]]
![[L11 Local Planning - RRT Spline Base planning-2.png]]
![[L11 Local Planning - RRT Spline Base planning-3.png]]
## Optimization for a solution
![[L11 Local Planning - RRT Spline Base planning-4.png]]
## A Sampling based planner
![[L11 Local Planning - RRT Spline Base planning-5.png]]
# Latice based planning
![[L11 Local Planning - RRT Spline Base planning-6.png]]
![[L11 Local Planning - RRT Spline Base planning-7.png]]
-  The F1tenth website provides a lot of literature in this regard
# Advanced local path planners
	![[L11 Local Planning - RRT Spline Base planning-8.png]]
# Graph-based planners
It is explain in the lectured but seems rather complex