[[L05 Follow the gap for obstacle avoidance]]
## List of functions
- Init: 
	- Initialises the object
- plan:
	1) Find closest points to Lidar
	2) Eliminate all points within the 'bubble' (Set to zero)
	3) Find max lenght gap
	4) Find the best point in the gap
	5) Publish drive message

- preprocess_lidar:
	1) Divide the lidar scans in its range
	2) Remove  data behind lidar [135;-135]
	3) Convolve input and normalise
	
		`>>> np.convolve([1, 2, 3], [0, 1, 0.5])`
		`array([0. , 1. , 2.5, 4. , 1.5])
		Convolve two matrices is a type of elementwise matrix multiplication. The kernal is flipped and shifted through the first array.
		`0 = 1 * 0`
		`1 = 1 * 1 + 2 * 0` 
		`2.5 = 1 * 0.5 +1 * 2 + 3 * 0`
		`4 = 3 * 1 + 2 * 0.5
		`1.5 = 3 *0.5`  
		Adding a second parameter; "same" to the function cuts of the output vector to be the same size as the original vector
		`array([1. , 2.5, 4.0 ])
		Convolution is applied to smoothing affect on the data and enhance the data:
		- Noise Reduction
		- Smoothing for better interpretation
		- Averaging over a window
		- Preventing spurious peaks
		
	4) Clips ranges
	5) Return ranges
	
- find_max_gap:
	1) Mask bubble
	2) Identify contiguous Non-bubble data
		Get a slice of each contiguous sequence (Parts that are not zero)
	3) Iterates over the slices in reverse order (Reverse more efficient)
		 (`slices[::-1]`).
	4) Finding the maximum gap
		For each slice `sl` the lenght `sl_len` is computed.
		If the the lenght of the current slice exceeds the threshold it is considered as a potential gap,
		The start and end of the chosen slice is then returned
	Note: The function returns as soon as as the threshold is met.It might not be the longest maximum gap

- find_best_point:
	- Takes the start, end and range of max gap
	1) Sliding window average
		- It smoothes the data and help the vehicle avoid sharp corners
	2) Max values is chosen in the average_max_gap
	3) The index is than adjusted by adding the start_i to get the index within the original lidar data

- get_angle:
	1) Convert the best point to a lidar angle to be used
	2) Clips the steering angle for the physical limit of the vehicle
	