## F1TenthSimBase
### Constructor
-  Initialises simulator parameters
- Creates instances of the `ScanSimulator2D, DynamicsSimulator and Centreline` classes
- Initializes various state variables, lap information, and history.
- Enables profiling using `cProfile`.
### Destructor
Disables profiling and  saves profiling results to a csv
Saves simulator history
### `step` Method
- Simulates a step in the simulator
- Checks for collision and map completion
### `build_observation` Method
- An abstract method that must be implemented by subclasses
### `check_lap_complete` and `check_vehicle_collision` Methods
- Helper methods for checking lap completion and vehicle collision.
### `reset` Method
- Resets simulator to initial state
### `save_data_frame` Method
- Saves history to a csv


## `F1TenthSim` and `F1TenthSim_TrueLocation` Classes:
### **Inheritance:**
- `F1TenthSim` and `F1TenthSim_TrueLocation` inherit from `F1TenthSimBase`.
### `__init__` Method:
- Initializes instances of the base class and sets up initial poses and scans.
### `build_observation` Method:
- Overrides the abstract method in the base class to implement observation building.
- Computes laser scans, vehicle speed, collision, lap completion, lap time, etc., as observations.

### Summary

These classes provide a modular and extensible framework for simulating the F1Tenth car, allowing for different types of observations and variations in simulation setups. The `F1TenthSim` class represents the simulator when the true vehicle location is not known, while `F1TenthSim_TrueLocation` includes the true vehicle state in the observation.