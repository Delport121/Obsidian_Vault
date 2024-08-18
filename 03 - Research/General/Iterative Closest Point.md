- An algorithm for calculating the displacement between scans

The ICP algorithm is based on a model where there are two point clouds, a source point cloud P = {p1, p2, p3, …, pm} and a target point cloud Q = {q1, q2, q3, …, qn }, both of which are subsets of R3. The goal of the algorithm is to find a transformation matrix T that minimizes the error E(T) between P and Q. The error E(T) can be represented by the following equation: 
![[Iterative Closest Point Eqn.png]]
where R is the rotation matrix, t is the translation matrix, p is the point in the source point cloud, and q is the nearest point in the target point cloud. R, t can be solved by minimizing the above error function. 
![[Iterative Closest Point min Eqn.png]]
The algorithm can be written as:
![[Iterative Closest Point.png]]
# ICP Variants
The Iterative Closest Point (ICP) algorithm is widely used for point cloud registration in robotics and computer vision. However, it has several shortcomings, including sensitivity to the initial value, high computational overhead, easily being trapped in a local optimal solution, and a lack of utilization of point cloud structure information. To address these issues, experts and scholars have proposed various improved ICP algorithms. 

One such improvement is the Point-to-Line ICP (PLICP) algorithm that replaces the point-to-point distance metric with point-line distance metric.This approach improves accuracy and requires fewer iterations but is more sensitive to initial values. Another improvement is the Point-to-Plane ICP (P2PL-ICP) algorithm, which uses the distance from the point to the surface instead of the distance from the point to the point to improve the convergence speed. 

The Generalized-ICP (GICP) algorithm combines P2P-ICP and P2PL-ICP into a probabilistic framework based on which point cloud matching is carried out. The covariance matrix eliminates some bad corresponding points in the solution process. GICP algorithm can effectively reduce the impact of mismatches and is one of the most effective and robust algorithms among many improved ICP algorithms. 

Other improvements include ICP using invariant features (ICPIF), Multi-scale ICP (MbICP), Normal-distributions transform (NDT), Continuous-ICP (CICP), Enhanced ICP, AA-ICP (using Anderson acceleration), and Robust ICP with Sparsity Induction Norms. 
# Reference
https://ignitarium.com/3d-lidar-slam-scan-matching-explained/
https://github.com/yuwwang123/LiDAR-Scan-Matching