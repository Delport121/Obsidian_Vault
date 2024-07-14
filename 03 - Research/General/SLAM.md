#SLAM
# Types of SLAM
[[https://medium.com/@nah[]()med3536/the-types-of-slam-algorithms-356196937e3d]]
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

In general SLAM shines in structured environments where dynamics are known.

### Graph based SLAM
Graph based SLAM treats the SLAM problem as a graph problem, where position information is represented by the nodes and the map is derived with the edges.
- Square root smoothing and mapping (Square root SAM):
	- Leverages the property that the SLAM graph is sparse (each node connected to few other nodes)
	- Represented as a graph were rows and columns represent nodes and entries represent edge connections between nodes. Thus the matrix will have many zeros and be considered sparse
	- Optimisation on a matrix can be made efficient using factorisation techniques
	- batch-based approach
- Incremental Smoothing and Mapping (iSAM):
	- Leverages factorisation similar to Square root SAM and allows incremental updates
	- More real-time approach and reduce computational resources required
- General frame work for graph optimisation (g2o):
	- 

Graph bases SLAM performs better than filtering SLAM when there are large uncertainties or non-Gaussian noises because of its flexibility, but it is computationally expensive.
### Deep learning SLAM
Solving the SLAM problem using neural networks and deep learning
- RatSLAM:
	- Base on a rat's brain
	- Good under certain conditions, but limited in generalizability
- LIFT-SLAM:
	- This algorithm focuses on SLAM with visual data and combines deep learning-based feature descriptors with traditional geometric feature descriptors.
- EnvSLAM:
	- This algorithm finds a trade-off between accuracy and efficiency, enabling a faster SLAM algorithm.
The limitations of deep learning based SLAM are typically in the computational requirements associated with deep learning and the generalizability of these algorithms.