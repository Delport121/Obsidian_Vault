#Python_F1tenth #Local_planning
This code defines a class named `LocalMPCC` which implements a Model Predictive Control (MPC) planner for local path tracking in a racing scenario. Here's a breakdown of the code:

1. **Importing Libraries**: The code imports several libraries including `numpy` for numerical computation, `matplotlib.pyplot` for plotting, `casadi` for symbolic computation and optimization, and specific modules from a custom package `f1tenth_benchmarks` including `LocalMapGenerator`, `LocalReference`, `BasePlanner`, and others.

2. **Constants Definition**: `NX` and `NU` are defined as constants representing the number of states and controls respectively.

3. **Class Definition**: The `LocalMPCC` class inherits from `BasePlanner`.

4. **Initialization**: The `__init__` method initializes the planner. It sets up various parameters, initializes data paths, initializes the local map generator, and prepares for optimization.

5. **Optimization Initialization**: The `init_optimisation` method initializes the symbolic variables and functions used in the optimization problem.

6. **Constraint Initialization**: The `init_constraints` method initializes the upper and lower bounds for state and control variables.

7. **Objective Initialization**: The `init_objective` method initializes the objective function to be optimized, which includes terms for minimizing contouring error, lag error, and steering input, and maximizing progress speed.

8. **Bounds Initialization**: The `init_bounds` method initializes additional constraints for the optimization problem.

9. **Solver Initialization**: The `init_solver` method sets up the optimization solver with the objective function, constraints, and solver options.

10. **Planning**: The `plan` method is the main function that generates a control action based on the current observations (such as sensor data). It sets up the optimization problem, solves it, and returns the computed control action.

11. **Helper Functions**: There are several helper functions like `generate_constraints_and_parameters`, `solve`, `filter_estimate`, `construct_warm_start_soln`, `plot_vehicle_controls`, and `plot_vehicle_position` which are used for various purposes such as setting up optimization parameters, solving the optimization problem, filtering estimates, plotting controls and vehicle position, etc.

12. **Utility Function**: `normalise_psi` is a utility function to normalize the angle `psi` within the range [-π, π].

	This class implements a model predictive control algorithm tailored for local path tracking in a racing scenario, with considerations for vehicle dynamics, path constraints, and optimization.