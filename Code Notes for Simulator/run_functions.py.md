
- simulate _laps
- 
- simulate_localisation_laps
	1) Resets the simulator and sets the initial pose
	2) Then the simulator runs in a while loop
		1) It takes and observation (From the particle filter) and plan the action
		2) The action is then fed into the simulator to simulate a step
		3) The particle filter is used to localise the robot and repeat the implementation in this while loop until it reaches the end of the simulation
	
- simulate_training_steps

- test_planning_all_maps
- test_planning_single_map

- test_full_stack_all_maps
- test_full_stack_single_map

 - test_mapless_all_maps
 - test_mapless_single_map