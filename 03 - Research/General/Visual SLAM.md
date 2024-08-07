# Lidar SLAM vs Visual SLAM
LiDAR [[SLAM]] uses 2D or 3D LiDAR sensors to make the map and localize within it. Generally, 2D Lidar is used for indoor applications while 3D Lidar is used for outdoor applications. Being a more mature sensor technology LiDAR SLAM comes with its own advantages of being the most accurate SLAM Technology, thanks to the active sensor used and the sensor fusion algorithms.  

On the other hand, Visual SLAM uses vision-based sensors: Monocular, Stereo and RGB-D Cameras. These techniques find application in various robotics applications including both indoor and outdoor robotics use cases.  

While LiDAR SLAM is more reliable, precise and prone to fewer errors, it has its drawbacks: 
- It demands a lot more compute power due to the type of data it handles 
- The infrastructure cost for the LiDAR and the associated hardware is comparatively expensive at this point of time 
- Other perception tasks including object detection and sign-board detection are much more complex  
- Lack of semantic information 

Visual SLAM is more appropriate in making autonomous robots with slow to medium speed.

# Types of VSLAM techniques
The principle of VSLAM is simple, the objective is to estimate sequentially the camera motions depending on the perceived movements of pixels in the image sequence. This can be done in different ways. One approach is to detect and track some important points in the image; this is what we call Feature-based VSLAM. Another one is to use the entire image without extracting features; such an approach is called Direct SLAM. Of course, other SLAM solutions also exist using different cameras such as RGB-D or Time-of-Flight (ToF) cameras (which provide not only an image, but also the depth of the scene), or event cameras (detecting only changes in the image). 
![[Visual SLAM.png]]
#### Feature-based SLAM
Feature-based SLAM can be divided again into two sub-families: filter-based, and Bundle Adjustment-based (BA) methods.  

While landmarks such as buildings and signposts are easily identified by humans, it is much easier for machines to identify and match low level features such as corners, edges, and blobs. More sophisticated feature definitions, together with detection algorithms and descriptors (a distinct feature representation) have been invented, such as Scale-invariant Feature Transform (*SIFT*), Speeded Up Robust Features (*SURF*) and Oriented FAST and Rotated BRIEF (*ORB*). These features are designed to be robust to translation, rotation, variations in scale, viewpoint, lighting, etc.   A limitation to the feature-based approach is that, once the features are extracted, all other information contained in the image is disregarded. This could be problematic when feature matching alone cannot offer robust reconstruction, e.g., in environments with too many or very few salient features, or with repetitive textures
#### Direct SLAM
In contrast to feature-based methods, direct methods directly use the image without any feature detectors and descriptors. Such feature-less approaches use photometric consistency to register two successive images (for feature-based approaches, the registration is based on the geometric positions of feature points). In this category, the most known methods are DTAM, LSD-SLAM, SVO, or DSO. Finally, with the development of deep learning, some SLAM applications have emerged to imitate the previously proposed approaches. Such research has generated semi-dense maps representing the environment, but direct SLAM approaches are time consuming and often require GPU-based processing.
#### RGB-D SLAM
The structured light-based RGB-D camera sensors recently became inexpensive and small. Such cameras can provide 3D information in real-time but are used for indoor navigation as the range is inferior to four or five meters and the technology is extremely sensitive to sunlight. One can refer to RGB-D VSLAM approaches.
#### Event camera SLAM
An event camera is a bio-inspired imaging sensor that can provide an “infinite” frame rate by detecting the visual “events,” i.e., the variations in the image. Such sensors have been recently used for V-SLAM. Nevertheless, this technology is not mature enough to be able to conclude about its performance for SLAM applications.
# Popular VSLAM algorithms
#### RTAB-Map
RTAB-Map stands for Real-Time Appearance Based Mapping. It has been distributed as an open-source library since 2013. RTAB-Map started as an appearance-based loop closure detection approach with memory management (shown in below figure) to deal with the large-scale and long-term online operation. It then grew to implement Simultaneous Localization and Mapping (SLAM) on various robots and mobile platforms. RTAB-Map supports both visual and LiDAR SLAM, providing in one package a tool that allows users to implement and compare a variety of 3D and 2D solutions for a wide range of applications with different robots and sensors. It uses depth images with RGB images to construct maps. The graph is created here, where each node contains RGB and depth images with corresponding odometry pose. The links represent the transformations between nodes. When the graph is updated, RTAB-Map compares the new image with all previous ones in the graph to find a loop closure. When a loop closure is found, graph optimization is done to correct the poses in the graph. For each node in the graph, we generate a point cloud from the RGB and depth images. This point cloud is transformed using the pose in the node. The 3D map is then created.
#### Deep learning in VSLAM
Geometry-based and Deep learning-based visual odometry paradigms.  
The geometry-based visual odometry computes the camera pose from the image by extracting and matching feature points.  
The deep learning-based visual odometry can estimate the camera pose directly from the data. For supervised visual odometry, it requires external ground truth as the supervision signal, which is usually expensive. In contrast, the unsupervised visual odometry uses its output as supervision signal. Besides, the local optimization module is optional for deep learning-based visual odometry.
#### ORB SLAM
ORB-SLAM is a real-time SLAM library for monocular, stereo and RGB-D cameras that computes the camera trajectory and a sparse 3D reconstruction. It can detect loops and re-localize the camera in real time. The system works in real-time on standard CPUs in a wide variety of environments from small hand-held indoor sequences, to drones in industrial environments and cars driving around a city. The back end based on bundle adjustment with monocular and stereo observations allows for accurate trajectory estimation with metric scale. The system includes a lightweight localization mode that leverages visual odometry tracks for unmapped regions and matches map points that allow for zero-drift localization. The main functionalities of ORB SLAM are feature tracking, mapping, loop closure and localization.
# Resources
https://ignitarium.com/visual-slam-possibilities-challenges-and-the-future/