Local map path planner

This code seems to be part of a system for local map-based path planning, likely for autonomous driving applications. Let's break down its key components and functionalities:

1. **Import Statements**:
    
    - The code imports necessary modules including `numpy`, `numba`, `trajectory_planning_helpers`, `interpolate` from `scipy`, and `os`.
2. **Class Definition - `LocalMapPP`**:
    
    - This class inherits from `BasePlanner`.
    - Constructor (`__init__`): Initializes the local map generator, and sets parameters for planning, such as whether to use a raceline.
    - Method `plan(obs)`: This method is called to plan the next action based on the observed environment. It generates a local track from the observed scan, then decides whether to use a raceline or follow the centerline. It then applies the appropriate planning strategy (`pure_pursuit_racing_line` or `pure_pursuit_center_line`) and returns the action.
    - Method `pure_pursuit_center_line()`: Implements the pure pursuit algorithm to follow the centerline of the track. It calculates a lookahead point on the track, computes the steering angle, and returns the action.
    - Method `generate_minimum_curvature_path()`: Computes the raceline using a local optimization approach for minimum curvature. It then fits a spline to the raceline.
    - Method `generate_max_speed_profile()`: Generates a maximum speed profile along the raceline based on vehicle dynamics and track curvature.
    - Method `calculate_zero_point_progress()`: Calculates the progress of the vehicle starting from a zero point (useful for lap counting).
    - Method `pure_pursuit_racing_line(obs)`: Implements the pure pursuit algorithm to follow the raceline. It calculates a lookahead point on the raceline, computes the steering angle and desired speed, and returns the action.
3. **Helper Functions and Numba-Decorated Function**:
    
    - `ensure_path_exists(path)`: Checks if a directory path exists and creates it if not.
    - `interp_2d_points(ss, xp, points)`: Interpolates 2D points based on a given array of x-values (`xp`) to obtain corresponding y-values (`points`) at specified x-values (`ss`).
    - `get_local_steering_actuation(lookahead_point, lookahead_distance, wheelbase)`: Numba-decorated function that calculates the steering angle based on the lookahead point, lookahead distance, and vehicle's wheelbase.
4. **Numba Decorators**:
    
    - `@njit(fastmath=False, cache=True)`: Decorates the `get_local_steering_actuation` function for just-in-time compilation with Numba, which can significantly speed up its execution.

Overall, this code appears to be a part of a complex system for local map-based path planning, which employs techniques like pure pursuit and spline interpolation for generating smooth and efficient trajectories. Additionally, the use of Numba optimizations suggests a focus on performance-critical computations.