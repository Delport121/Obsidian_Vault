# Types of SLAM
[[https://medium.com/@nahmed3536/the-types-of-slam-algorithms-356196937e3d]]
### Filter based SLAM
The SLAM problem is seen as a state estimation problem.As more date is collected the estimate is augmented and refined
- Kalman filter: 
	- Consist of two steps (Prediction and update)
	- The filter assumes a linear world with Gaussian error which is also its main limitation
- Extended Kalman Filter (EKS):
	- Extend Kalman filter by using linearisation. It involves Taylor series expansion and keeps most of the Kalman filter's functionality.
	- Very popular for non-linear state estimation due flexibility and efficiency, but it can also introduce errors in the estimate and lead to sub optimal performance
- Unscented Kalman Filter (UKS):
	- Relax's the linearity assumption by approximating the probability distribution.
	- Provides more accurate estimates but can be computationally expensive
- Particle Filter:
	- Represesent the state as a set of particles where each particle represent a state. As more information is collected the particles are rewieghted to match the observed measurements
	- Limitation include the particles diverging from the true state and the algorithm being computationally expensive

In general SLAM shines in structured environments where dynamics are known

### Graph based SLAM
### Deep learning SLAM
Solving the SLAM problem using neural networks and deep learning