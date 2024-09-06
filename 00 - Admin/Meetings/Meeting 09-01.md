# What I have done so far
- Tried cubic curve fitting instead of using splines
	- Does okay, but struggles with tight turns
	- Cannot define a fit for a non-function line -> more than 1 y value for a single x
- Full map curvature
	- Played around with your code
	- The local map curvature has some correlation, at least in amplitude.
	- Maybe apply scan matching to this and see if it can match the local scan to the big one
# Questions for Ben
- Should the curvature extraction be for the predicted curves aswell?
- The range and bearing representation seem to be towards a single point in the map. So each curve will then have something like a anchor point?
- Both lines or should I maybe just look at the centre line?
- More info on correspondence. Kinda understand, but I feel like I'm missing something
- Discuss the line extraction algorithms and using them for curvature
### Current issues
- I need some kind of centroid or single point to identify curves with to store it in the localisation algorithm
- Some form of segmentation of the curves. I fee
- Do I use some form of scan matching for the curvature lines extraction?
	- I do not know how robust this method of curvature extraction will be in later stages
