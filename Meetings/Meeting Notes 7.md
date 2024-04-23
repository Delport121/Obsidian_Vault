## Notes and Questions for Ben

- The race track generator for pure pursuit does not work for the updated simulator. It does not find the minimum curve csv folder. Upon closer inspection it does not seem that there is such a folder in the directory at all.
- 
- MPCC works but requires IPopt. This is mentioned in the readme, but the link takes you to Benjamin's repo. I got it running, but it still wants the IPopt thing. I have not gone to deep into this as it a bit overwhelming and i still need to figure out the basics

- I see there is an assignment 2 and 3 in the sensor fusion repo? Was there an assignment 1 as well?
	- Also I have been running into some errors with. Specifically the one line off code:
	```powershell
((SFusion) ) ruan@ruan-OptiPlex-7050:~/Documents/sensor_fusion$ /home/ruan/Documents/sensor_fusion/SFusion/bin/python /home/ruan/Documents/sensor_fusion/RoverTests.py
Deadreckon MAE: 4.6842 m --> Estimated MAE: 0.7679 m
Traceback (most recent call last):
  File "/home/ruan/Documents/sensor_fusion/RoverTests.py", line 56, in <module>
    test_ekf()
  File "/home/ruan/Documents/sensor_fusion/RoverTests.py", line 35, in test_ekf
    plot_estimation_belief(ekf_robot, ekf)
  File "/home/ruan/Documents/sensor_fusion/sensor_fusion/utils/utils.py", line 48, in plot_estimation_belief
    arc = pat.Arc((mean[0],mean[1]),major,minor,angle,color="0.5")
TypeError: Arc.__init__() takes 4 positional arguments but 5 were given
```
Simply replace the line 48 with
```python
arc = pat.Arc((mean[0], mean[1]), major, minor, angle=angle, color="0.5")
```
This seemed to work, but it does not make sense why it would cause an issue. I was unable to fix this where it was used in the assignments in jupyter
- Furthermore it seems that the four executable files must be one directory higher than where they are placed in the repo.

- Have you used the ros simulator for anything specific and did you actually build on top of it?
- How far along should I be by know? 
- What is the rough time budget for the remaining things such as the particle filter and SLAM algorithm 
(I am worried that I am not making enough progress fast enough) 

# Meeting questions
- Apologies for missing journal club again
- Task tracker for aquasitions

## What have I done
- Looked at SLAM once again (Specifically the different types)
- Matlab autonomous navigation part 2,3....
- Bayes rule and markov principle
- I had to go through Bens stuff again to understand the sensor fusion and the different filter. I am finding it rather difficult to understand the algorithms
- Find something that peaked my interest regarding autonoums rally racing. It has a ros repository but the setup for this will likely be tedious once again.
## Plan for next week:
- [x] Lectures Thursday and Friday (Its about Kalman filters, hopefully its worthwhile)  [completion:: 2024-04-21]
- [x] Do the assignments in Ben's repo?  [completion:: 2024-04-17]
      Unfortunately not possible since it is incomplete, but the theory remains usefull
- [ ] I am looking to implement simple algorithms of the particle filter and Slam for a fundamental understanding.  I am finding it rather difficult to jump directly into the F1tenh Gym. This may take some time though
- [x] Continue research in regards to where there a gaps in the industry (Such as the fast image processing for racing)  [completion:: 2024-04-22]
	- [x] Look at linkdin saves posts  [completion:: 2024-04-22]
	- [x] Look at bookmarks  [completion:: 2024-04-16]
- [ ] I want to mess with ros more and perhaps take a from scratch approach, so I do not run into issues later on (Lidar etc)
- [x] Setup latex template for note taking aspect of thesis (Remember Altus send something)  [completion:: 2024-04-22]
- [x] Chapter outline for a direction to discuss objectives. This is to brake down the masters into smaller problems  [completion:: 2024-04-23]
- [x] Understand particle filter  [completion:: 2024-04-22]
	- Probalist robotics helped with finally understanding it

What is my contribution? Keep focus
Look on research on autorally, what they do etc