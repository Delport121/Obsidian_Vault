# Steps to Apply Transformations for Odometry Correction and Map Building

## 1. Initial Pose and Odometry
- Start with an initial robot pose in the global frame, typically $[x, y, \theta] = [0,0,0]$\.
- Use odometry (e.g., wheel encoders, IMU) to predict the next pose incrementally as the robot moves.

## 2. Relative Transformations from Scan Matching
- Perform **scan-to-scan matching** (e.g., ICP or NDT) between consecutive scans to compute the relative transformation $T_{scan}$ between the current scan and the previous scan:
$$\begin{equation} T_{\text{scan}} = \begin{bmatrix} \cos\theta & -\sin\theta & x \\ \sin\theta & \cos\theta & y \\ 0 & 0 & 1 \end{bmatrix} \end{equation}$$

where \( x, y \) are the translation offsets and \( \theta \) is the rotation angle.

## 3. Correct Odometry with Scan Matching
- Combine the odometry-based transformation $T_{odm}$with the scan-matching correction $T_{scan}$ to update the robot's global pose:

$$
T_{\text{global}}^{k} = T_{\text{global}}^{k-1} \cdot T_{\text{scan}}
$$

- This corrects drift in the odometry by aligning the scans.

## 4. Incremental Map Construction
- For each scan, transform the scan points into the global frame using the corrected pose:

$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}
=
T_{\text{global}} \cdot 
\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$

- Add the transformed points to the global map.

## 5. Loop Closure
- Detect revisits to a previously mapped location (e.g., by comparing the current pose with prior poses).
- Perform **scan-to-map matching** to compute a correction transformation  $T_{loop}$
- Apply $T_{loop}$ to adjust the robot’s pose graph and refine the map.
