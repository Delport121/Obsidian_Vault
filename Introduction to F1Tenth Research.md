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
- [ ] Study repo

# Introductory tasks
- [ ] Implement follow the gap
- [ ] Implement a pure pursuit controller to follow centre line
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
	- [ ] 1)
	- [ ] 2)
	- [ ] 3)
	- [ ] 4)
	- [ ] 5)
	- [ ] 6)
	- [ ] 7)
	
