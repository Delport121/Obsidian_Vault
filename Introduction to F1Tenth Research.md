# General software skills
- Python programming Git 
- this is essential Robot operating system (ROS2) 
- Clean code other people should be able to understand JIT 
- jist in time compiled code. This makes python code a lot faster. Look at the JAX or Numba libraries 
- Good data visualisation - when you read an article, look at how the results are presented. You should learn to make clean graphs that clearly make a point

# Python simulator
- [x] Clone repository
- [x] Run follow the gap
- [x] Generate racing line
- [x] Track it with pure pursuit algorithm
- [x] Study repo

# Introductory tasks
- [x] Implement follow the gap
- [x] Implement a pure pursuit controller to follow centre line  [completion:: 2024-03-06]
	- Track centre line at constant speed
	- Tune lookahead distance
	- Evaluate tracking accuracy
	- Run an experiment to see how accuracy changes with speed
	- best tracking with a speed of 5m/s

# Ros skills
- [ ] Follow skills course

1) Ideation
2) Sandbox development
3) Scale implementation
4) Evaluation
5) Write up

# Personal
Expand the current method into a localisation and mapping algorithm

## Objectives
- Expand racing with local maps into a localisation system that can be used to estimate the vehicles location
- Expand local map to a SLAM algorithm to fuse local map together
- Test algorithms on F1Tenth
- Implement algorithms on a different platform

## Starting steps
- [x] Study Optimisation-based Control in Unmapped Environments - The Local Map Framework for Autonomous Racing
	- [ ] Study code in localmap_racing folder

- [ ] Study state estimation theory
	- [ ] https://github.com/BDEvan5?tab=repositories
	- [ ] Roughly be able to recode examples
	- [ ] Book to read "Probalist robotics"
	- [ ] F1Tenth lectures on scan matching
	- [ ] Youtube resources

- [ ] Reimplement particle filter for F1Tenth racing
	- [ ] Experiment to maximise localisation performance
	- [ ] Recreate sensor model used in https://github.com/f1tenth/particle_filter
	- [ ] Write in JAX libraries
	- [ ] Look at numba library
	
- [ ] Start to adapt the local map racing method into a localisation method
	- Do it mathmatically
	- Use the curvature of the inner and outer boundaries to check where the vehicle is at each time step
- [ ] Reading
	- [ ] [Vehicle dynamics state estimation and localization for high performance race cars](https://www.sciencedirect.com/science/article/pii/S2405896319303957)
	- [x] [ROS-based localization of a race vehicle at high-speed using LIDAR](https://www.e3s-conferences.org/articles/e3sconf/abs/2019/21/e3sconf_icpeme2018_04002/e3sconf_icpeme2018_04002.html)  [completion:: 2024-02-28]
		[[ROS_based localization of a race vehicle at highspeed using LIDAR.pdf]]
	
	- [x] Accurate Mapping and Planning for Autonomous Racing
	      https://ieeexplore.ieee.org/abstract/document/9341702?casa_token=VeSlTFSJFPsAAAAA:XKLNhTaQSBvh__9Jdau_YvyV_P5Cg6k6o2xr7Gln5usg83_A2kpSoGTcq4eqYqxZJr9S3Jdl5rMY
	      [[Accurate_Mapping_and_Planning_for_Autonomous_Racing.pdf]]
	      
	- [ ] formula student driverless
	- [ ] [AMZ driverless: The full autonomous racing system](https://onlinelibrary.wiley.com/doi/abs/10.1002/rob.21977)
	- [ ] TUM autonomous motorsport: An autonomous racing software for the Indy Autonomous Challenge
	      https://onlinelibrary.wiley.com/doi/full/10.1002/rob.22153