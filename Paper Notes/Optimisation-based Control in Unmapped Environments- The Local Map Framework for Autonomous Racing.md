
The paper proposes a method of un-mapped racing algorithms. Various algorithms are tested 
"Our two-stage local map planner achieves lap times 3.22% faster than end-to-end agents trained with the TD3 algorithm and 8.8% faster than the follow-the-gap method."

"The primary improvement source is the local map planner’s access to a vehicle dynamics model that can be optimised. The com- parison with global planning approaches showed an average of 3.28% slower lap times, resulting from limited planning horizon around corners and thus reduced speed. C"


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
### B) Optimisation planners
#### 1) Two stage optimisation planner
Uses pure pursuit 
#### 2) Model Predictive Contouring Control (MPCC)



## Conclusion
### Applications
- Image-based Control
- Local Map Fusion for High-speed SLAM
- Safe Reinforcement Learning
