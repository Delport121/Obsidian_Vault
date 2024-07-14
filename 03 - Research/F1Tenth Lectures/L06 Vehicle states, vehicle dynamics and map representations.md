#Vehicle_states #Vehicle_dynamics #Lectures

It is probably best to look at the actual lecture slides as it provides good visuals
# Vehicle states
- Position
- Heading
	- Usually with respect to the x-axis
- Frenet frame
	- Moving coordinate system determined by a tangent line and curvature (Raceline)
	- s -  runlenght
	- d - lateral position relative to reference path (Measured on normal vector)
		- Positive left and negative right
	- Used for track progress
- Velocity
	- Absolute velocity $$v_{abs} = \sqrt{v_{x}^2+v_{y}^2}$$
- Acceleration
	- Longitudinal $a_{x}$ - increase/decrease of speed
	- Lateral $a_{y}$ - Left and right steering
- Steering angle ($\delta$)
	- Defined respective to centre line of agent
- Other states
	- Includes pitch, roll and yaw.
	- Any angular velocity or acceleration along Cartesian coordinates
- Vehicle dynamics:
	- Sideslip angle ($\beta$) - Drifting, moving sideways, high velocity not alligned with the wheels
	- Slip angle ($\alpha$)  - Occurs at the tires, creates as lateral tire force, angle between tire direction and moving direction of the contact plane
	- Wheelslip ration($s$) -  Difference between velocity tires and the vehicle motion
# Vehicle dynamics modelling
- Typical matrix representation
- LTI: Linear time invariant - system dynamic do not change with time
- Time-varying systems: Changes with time

Vehicle dynamics model types:
	- Single track model
	- Double track model
	- Multi-body Simulation
	- Finite elements simulation

- Kinematic single track model
- Linear single track model
- Nonlinear single track model
- Double track model
Vehicle dynamic simulation:
	- Open-loop maneuver
	- Closed-loop maneuver

## Map Representations
Each map representation has a different implementation in mind based on its advantages and disadvantages
- Occupancy grid map: For smaller robots
	 ![[Pasted image 20240531171158.png]]
- Point cloud: real world application
	 ![[Pasted image 20240531171416.png]]
- Feature map: Used for localisation
	 ![[Pasted image 20240531171557.png]]
- Semantic map: Used for object detection
	 ![[Pasted image 20240531171656.png]]
- High definition map: Uses all sensor and features
	 ![[Pasted image 20240531171730.png]]