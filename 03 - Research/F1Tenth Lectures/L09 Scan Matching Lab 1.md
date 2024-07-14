#Scan_matching #Lectures
## Input 
- Reference scan
- Current scan
- Initial guess of roto-transformation
## Output
- Transformation q (Converged solution)

## Method
At $t=k$ 
1) Use previous guess $q_{k}$, transform coordinates of current scan into frame of previous scan
2) For each point, find closest line segment (Correspondence search
3) )  Update transform
   a. Formulate point to line error objective
   b. Find transform $q_{k+1}$ that minimises objective
4) Repeat until convergence