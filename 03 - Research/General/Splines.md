# Basics
- Splines minimises the bending energy![[Splines.png]]![[Splines-1.png|left]]![[Splines-2.png]]
## Solving cubic splines
### General form for solving points
![[Splines-3.png]]
### General form for solving specified tangents
![[Splines-4.png]]
### Catmull-Rom Spline
![[Splines-5.png]]
This is the same as interpolating a continuous function by sliding a cubic function
C1:
	- Continuous
	- Continuous derivative
- Local control
### Natural cubic Spline
-minimises energy function
![[Splines-6.png]]
C2:
	- Continuous
	- Continuous derivative
	- Continuous 2nd derivative
### B-Spline
- C2
- Local control
- Does not interpolate
![[Splines-7.png]]
## 2D Functions
![[Splines-8.png]]
![[Splines-9.png]]
# References
https://www.youtube.com/watch?v=YMl25iCCRew&t=52s