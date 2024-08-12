## 1) Understand the Purpose of Comments
- **Clarify Complex Logic:** Comments should explain why the code does what it does, especially when the logic is non-trivial.
- **Document Assumptions:** If your code makes specific assumptions, note them. This is crucial in research, where assumptions may change.
- **Guide Future Developers:** Think of comments as a conversation with your future self or team members. Ensure they can understand the context and reasoning behind the code.
## 2) Types of Comments
#### Inline Comments:
- Use for specific lines or blocks of code that may be unclear.
- Keep them brief and to the point.
- Example:
```python
result = complex_calculation(x, y) # Adjusted for non-linear behavior in edge cases 
```
#### Block comments:
- Place at the beginning of a function, class, or significant block of code.
- Summarize what the block of code does and why it’s important.
- Example:
```
# This function implements a Kalman filter to estimate the position
# of the vehicle. It is optimized for real-time processing on embedded systems.
```
#### Docstrings:
- Use in Python for modules, classes, and functions.
- Provide a detailed explanation of what the code does, input/output parameters, and any exceptions raised. 
	- This is especially important in instances where one variable may contain list of other variable (such as a python tuple or arrays of values representing different parameters). 
	- For simple or very "obvious" functions, this may prove to be excessive, thus use your own judgement on this. 
- Example:
```python
def filter_noise(data):
    """
    Filters out noise from the sensor data using a moving average.
    
    Parameters:
    data (list): List of sensor readings.
    
    Returns:
    list: Filtered sensor data.
    """
```
#### TODO Comments:
- Mark parts of the code that need further development or where improvements can be made.
- Use a consistent format like `# TODO:` to make them easily searchable.
- Example:
```python
# TODO: Optimize this loop for large datasets
```
#### Variable declaration comments:
- Group similar or associated variables together and provide a comment of their purpose
- If a variable contains information about various parameters, provide a short description of what it contains.
- Example:
```python
# Car pose
self.x = None
self.y = None
self.theta = None

# Partcles poses and weights
self.particles = np.zeros((self.MAX_PARTICLES, 4)) #Containes x, y, heading, particle weight
```
#### Step comments:
- Since we are working with algorithms, it is important to know when a a certain step in the algorithm is happening. As such provide comments to clearly show when a step in the algorithm is happening.
- Example:
```python
    def MCL(self, a, o):
        '''
        Performs one step of Monte Carlo Localization.
            1. resample particle distribution to form the proposal distribution
            2. apply the motion model
            3. apply the sensor model
            4. normalize particle weights

        This is in the critical path of code execution, so it is optimized for speed.
        '''
        if self.SHOW_FINE_TIMING:
            t = time.time()
        # draw the proposal distribution from the old particles
        proposal_indices = np.random.choice(self.particle_indices, self.MAX_PARTICLES, p=self.weights)
        proposal_distribution = self.particles[proposal_indices,:]
        if self.SHOW_FINE_TIMING:
            t_propose = time.time()

        # compute the motion model to update the proposal distribution
        self.motion_model(proposal_distribution, a)
        if self.SHOW_FINE_TIMING:
            t_motion = time.time()

        # compute the sensor model
        self.sensor_model(proposal_distribution, o, self.weights)
        if self.SHOW_FINE_TIMING:
            t_sensor = time.time()

        # normalize importance weights
        self.weights /= np.sum(self.weights)
        if self.SHOW_FINE_TIMING:
            t_norm = time.time()
            t_total = (t_norm - t)/100.0

        if self.SHOW_FINE_TIMING and self.iters % 10 == 0:
            self.get_logger().info(str(['MCL: propose: ', np.round((t_propose-t)/t_total, 2), 'motion:', np.round((t_motion-t_propose)/t_total, 2), \
                  'sensor:', np.round((t_sensor-t_motion)/t_total, 2), 'norm:', np.round((t_norm-t_sensor)/t_total, 2)]))

        # save the particles
        self.particles = proposal_distribution
```