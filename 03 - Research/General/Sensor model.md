## Beam models of range finders
This model is an approximate physical model of real range finders. The parameters that shape the overall distribution are reffered to as intrinsic parameters.
#### Correct range with local measurement noise
This is represented by a normal Gussian distribution.
#### Unexpected objects
This is represented by a exponential distribution. The likelihood of sensing unexpected objects decreases with range.
#### Failures 
Sometimes objects are missed altogether due to issues like specular reflections. A typical result of sensor failure is a max-range measurement. This is represented with a high likelihood at the max range of the sensor.
#### Random measurements
Sometime range finders produce entirely unexplained results. This is modelled as a uniform normal distribution
## Likelihood fields for range finders
A type of 'ad hoc' algorithm that lacks a plausible physical explanation, but works well in practice
*Advantages:*
	- Smoothness
*Disadvantages:*
	- Does not explicitly model people or other dynamics that might cause short readings
	- Treats sensor as if they can see through walls
	- Does not take map uncertainty into account (Cannot handle unexplored areas)
## Correlation-based measurement models
Takes a local map to global map approach
## Feature-Based Measurement models
Models each landmark with its range, bearing and additional information regarding the feature. The way in which additional information is displayed can take many forms.
### Sensor model with known correspondence
[[Data association problem]] A key problem with range and bearing sensors. This problem arises when landmarks cannot be uniquely identified, so that some residual uncertainty exist with regards to the identity of the landmark.

It is thus useful to introduce a [[Correspondence variable]] between the feature and the landmark in the map. The variable is the true identity of an observed feature. 

# References
- Probabilistic robotics