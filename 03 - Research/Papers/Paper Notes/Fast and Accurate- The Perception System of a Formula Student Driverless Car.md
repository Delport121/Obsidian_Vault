[[Fast_and_Accurate_The_Perception_System_of_a_Formula_Student_Driverless_Car.pdf]]

The paper describe the fusion of 3D lidar data and camera for autonomous racing. 

-  The Lidar pipeline uses a GPF algorithm and Euclidian clustering to process the original point cloud data 
- The also adopted YOLO3 target detection

The paper describes it contribution as follows:
- A fast and accurate cone detection method based on YOLOv3 with attention module and vision-based boundary detection for track cones.
-  LIDAR pipeline including fast ground segmentation, point cloud cluster, and cones filter based on cones’ shapes.
- A data fusion method that suits the FSAC track.

## Methodology
### A)  Binocular Camera Pipeline
1) YOLOv3- Based cone detection
2) Vision-Based boundary Regression and Drivable lane segmentation

### B) Lidar Cone detection
1) Fast ground segmentation
2) Cone Cluster
3) Data Fusion

## Results

The preposed method showed great improvement overall.
##### New Words
YOLOv3
Ground segmentation
Euclidian clustering
GPF algorithm