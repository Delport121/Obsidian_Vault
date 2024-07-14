#Visual_SLAM #Computer_Vision #Lectures
# Vision Hardware
- Cameras
- Lidar
	- Mechanical
	- Solid state
- Intel Realsense D435i

Relevant specs:
- Shutter type
- Rollling vs global
- Sensor size and pixel size
- Field of view
- Connector
- Image signal processor (ISP)
- Distortions
- Lens aberrations
	- Spherical aberrations and field curvature
	- Chromatic aberration (colour shift) 
# Accessing the camera on linux
![[L12 Vision 1 - Classic methods.png]]
```bash
ls /dev/video*
v412src
v412-ctl -d /dev/video2 --list-ctrls-menus
	v412-ctl -d /dev/video2 --list-formats-ext
```
# Cameras model and calibration
![[L12 Vision 1 - Classic methods-1.png]]
![[L12 Vision 1 - Classic methods-2.png]]
![[L12 Vision 1 - Classic methods-3.png]]
-  OpenCV has a tutorial for getting the intrinsics and general calibration
![[L12 Vision 1 - Classic methods-4.png]]
## Distance estimation
![[L12 Vision 1 - Classic methods-5.png]]
![[L12 Vision 1 - Classic methods-6.png]]
# Detection with OpenCV
## Edge and blob detection
![[L12 Vision 1 - Classic methods-7.png]]
## HSV colour space
![[L12 Vision 1 - Classic methods-8.png]]
- Example of lawnmower edge detection
![[L12 Vision 1 - Classic methods-9.png]]
## Feature extraction
- Feature extraction require special filters to respond to them
## 2D Convolution
![[L12 Vision 1 - Classic methods-10.png]]
### Some classical extraction methods
![[L12 Vision 1 - Classic methods-11.png]]
- SIFT is slow
	- ORB is good as it can track rotated objects and is fast
# Visual SLAM
![[L12 Vision 1 - Classic methods-12.png]]
## Bundle adjustment
![[L12 Vision 1 - Classic methods-13.png]]
![[L12 Vision 1 - Classic methods-14.png]]
![[L12 Vision 1 - Classic methods-15.png]]
# References
[Visual SLAM](https://medium.com/@dcasadoherraez/introduction-to-visual-slam-chapter-1-introduction-to-slam-a0211654bf0e)