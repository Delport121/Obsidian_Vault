There is different degrees of difficulty regarding localisation problems. There are four main dimensions to this problem.
## 1. Global vs local localization
- *Position tracking* assumes the robot's initial pose is known
- *Global localisation* does not know the robot's initial pose on the map
- *Kidnapped robot problem* suggest that the robot is picked up and teleported somewhere else on the map. The idea arises from the fact that localisation algorithms cannot be guaranteed never to fail. Thus, by initialising this problem, it shows the algorithm's ability to recover from global localisation failures.
## 2. Static vs dynamic environments
*Static environments* are environments where only the only variable quantity (state) is the robot's pose.
*Dynamic environments* suggest that objects other than the robot's pose may change over time. In such instances, [[Markov's assumption]] may be justified. Another approach is to filter out dynamic data.
## 3.Passive vs active localisation
*Passive localisation:* The localisation module only observes the robot operating.
*Active localisation:* These algorithms control the robot so as to minimise the local-
ization error and/or the costs arising from moving a poorly localized robot
into a hazardous place.
## Single robot vs multi-robot
Multi robot localisation a result in non-trivial solution as one robot's can be used to bias another robot and improve localisation. It does however introduce concepts such as collision avoidance and communication

There are two main categories of localisation called [[Markov localisation]] and [[Monte Carlo Localisation]]