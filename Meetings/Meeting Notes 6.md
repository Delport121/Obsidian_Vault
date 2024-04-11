2024-04-10
# Questions
## Ben
- The race track generator for pure pursuit does not work for the updated simulator. It does not find the minimum curve csv folder. Upon closer inspection it does not seem that there is such a folder in the directory at all.

- MPCC works but requires IPopt. This is mentioned in the readme, but the link takes you to Benjamin's repo. I got it running, but it still want the IPopt thing

- I am struggling to run the state estimation folder code. Its missing the file directory yet I am in the correct directory? (Solved)
```powershell
ruan@ruan-OptiPlex-7050:~/Documents/sensor_fusion$ /bin/python3 /home/ruan/Documents/sensor_fusion/sensor_fusion/RoverTests.py
Traceback (most recent call last):
  File "/home/ruan/Documents/sensor_fusion/sensor_fusion/RoverTests.py", line 2, in <module>
    from sensor_fusion.utils.Gaussian import Gaussian
ModuleNotFoundError: No module named 'sensor_fusion'
```
I tried a virtual environment aswell, but this also did not solve the problem.
Checked the import folder structure in other folder such as the benchmark one. Its the same but works?
#### Update1 
Manage to solve the issue. Two things must be done
	- Move the for executeble folders one directory higher than their intitial location
	- When the rover one is executed, you may get the following error
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

- What are the assignment in the sensor fusion repo? Would i be a good idea to see if I can do it roughly to test my understanding? Are they to be used in Jupyter notebook?

- Will I be able to visualise my algorithms with the f1tenth ros simulator  

# What have I done:
- Work on modules (Had block modules last week)
- Pocket Cube stuff
- Spoke with Cyberate people a bit
- Looked at more particle filter stuff and trying to understand it well
- Got slam and nav running in ros

- Went trough Ben's sensor fusion repository. The notes are good though and will be especially helpful for the coding stuff l

# Plan for next week:
- Start looking at the examples and start roughly recoding (If )
 - Do some research in regards to where there a gaps in the industry (Such as the fast image processing for racing)
 - Maybe add a lidar to the model and look at nav2? (SLAM stuff since this relates to what I have to do)
 - Look at slam (NB)
 - Setup latex template for note taking aspect of thesis

Slam for ros
What is my contribution? Keep focus
Dont try to recode, only if necessary
Plan for benjamins questions, so he can 

Get the basic stuff working, SLAM and path planning
Start looking at the gaps in industry or entry points
Ask ben questions

