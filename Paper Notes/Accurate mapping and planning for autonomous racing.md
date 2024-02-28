[[Accurate_Mapping_and_Planning_for_Autonomous_Racing.pdf]]

The paper present a perception, mapping and planning pipeline implementation. It combines lidar and camera data for sensor fusion with a layered mapping  approach that uses Bayesian filtering. This achieves high speed driving in unmapped environments. 

The pipeline enables the raise of maximum driving speed fro 3 to 12 m/s with a RSME of 0.29 m.

##### Why unknown race track is challenging for SLAM:
- High-speed motion is more uncertain which causes higher drift between sensor readings
- Horizon over which the upcoming dynamic motion must be planned scales with speed

# Method
## Autonomous Driving pipeline
![[Pasted image 20240207114937.png|400]]

- Significant noise is present when detecting distant cones

New words:
 - Local map
 - Global map
 - GraphSLAM
 - Bayesian inference