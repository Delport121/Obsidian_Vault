[[High performance racing on unmapped tracks using local maps.pdf]]

The paper proposes a method of un-mapped racing algorithms. Various algorithms are tested 
"Our two-stage local map planner achieves lap times 3.22% faster than end-to-end agents trained with the TD3 algorithm and 8.8% faster than the follow-the-gap method."

"The primary improvement source is the local map planner’s access to a vehicle dynamics model that can be optimised. The com- parison with global planning approaches showed an average of 3.28% slower lap times, resulting from limited planning horizon around corners and thus reduced speed. C"

## 1) Intro
- Map based methods are limited to cases where maps can be seen and planned prior to racing. (Classical racing)
- Mapless method does not require a map but typically has poor performance (Reactive methods and end-to-end neural networks)

- 
## Literature
### Classical racing
- Classical racing methods uses perception, planning and control pipeline 
- Racing tracks are mapped using SLAM which requires a slow pass around the track
- Particle filters a limited by requiring a map of the track
- Optimal control strategies typically require a map of the track
### Mapless racing
 - FTG (follow the gap) -No inherent speed control and thus cannot perform at  vehicle limits
 - Neural network - High crash rates, simulation to reality gap, jerky action


## Methodology
### A) Local map extraction
The algorithm ties point data from the lidar together based on the maximum track width to creat track segment. It is also capable of predicting some of the segments, such as a the release after a corner.
 - Tests that were done:
	 - Local map extraction
	 - Racing performance
	 - Computational requirements
###  B) Optimisation planners here that eu
-Local map extraction

#### 1) Two stage optimisation planner
Uses pure pursuit 
#### 2) Model Predictive Contouring Control (MPCC)



## Conclusion
### Applications
- Image-based Control
- Local Map Fusion for High-speed SLAM
- Safe Reinforcement Learning
