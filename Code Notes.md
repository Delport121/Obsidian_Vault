# Pure pursuit

# Follow the gap
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
		Convolv two matrices is a type of elementwise matrix multiplication. The kernal is flipped and shifted through the first array.
		`0 = 1 * 0`
		`1 = 1 * 1 + 2 * 0` 
		`2.5 = 1 * 0.5 +1 * 2 + 3 * 0`
		`4 = 3 * 1 + 2 * 1`
		`1.5 = 3 *0.5`  
		Adding a second parameter; "same" to the function cuts of the output vector to be the same size as the original vector
		
	4) Clips ranges
	5) Return ranges
	