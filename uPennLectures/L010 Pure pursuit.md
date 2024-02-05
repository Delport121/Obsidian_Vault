### The planning module
Mission planner 
-  What the is the overall goal of the vehicle
Behavioral planner 
- What rules should the vehicle follow in different situations
Local Planner 
- What is the optimal trajectory from position to goal

### Pure pursuit
#### Assumptions
- Given a sequence of 2D waypoints
- Vehicle knows where points are in vehicles frame of reference (Can localize itself)
- Goal is to follow the points

- Use righthand coordinate system always
###  The Math

$$r = \frac{L^{2}}{2*|y|}$$
![[Pasted image 20240129082654.png]]
### How do we get the steering angle?
- Curvature is the inverse of radius
- Thus steering angle proportional to the curvature of the arc

$$\gamma = \frac{1}{r} = \frac{2*|y|}{L^2}$$
### Picking a goal point
1) Pick waypoint that is closest to vehicle
2) Go to the waypoint until you get to one that is one look ahead distance away from the car
3) Use that as the current waypoint
### Updating the goal point
1) Find the current waypoint
2) Actuate to the waypoint with the calculated steering angle
3) Localize to find the new pose, repeat
### Effect of changing the lookahead distance $L$
- Small L: Aggressive
- Large L: Smoother but larger trajectory tracking errors
![[Pasted image 20240129083742.png]]

### Notes
 - The waypoint are a sequence of position and could have a velocity component attached to them
 - The proportional gain $\frac{2}{l_{d}^2}$ can be tuned at different speeds ($l_{d}$ a function of vehicle speed)
 - Pure pursuit does not take dynamic into account

### The pure pursuit pipeline
1) Create a map using SLAM in ROS
2) Create a list of waypoints using a global planner
3) Pick waypoint to track at each frame
4) Set steering angle to track the current waypoint
5) Update the waypoint to track as you go
