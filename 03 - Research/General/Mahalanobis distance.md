The Mahalanobis distance is a distance measure  between a point and a distribution. The Mahalanobis distance takes into account the correlation between the variables.

For normal distance measures the distance of both points to the centroid is the same:
![[Mahalanobis distance.png]]But in the case of the mahalanobis distance:
![[Mahalanobis distance-1.png]]
*Equation*
$$MD = \sqrt{ (\vec{x}-\vec\mu{})^TS^{-1}(\vec{x}-\vec\mu{}) }$$
Where x  is the point coordinates and mu the centroid cordinates of the data. S is the covariance matrix of the data.

Say we generate a 95% error ellipse:
![[Mahalanobis distance-2.png]]Then all distances on the ellipses line is 2.45
![[Mahalanobis distance-3.png]]
# References
https://www.youtube.com/watch?v=xXhLvheEF7o&list=WL&index=20
