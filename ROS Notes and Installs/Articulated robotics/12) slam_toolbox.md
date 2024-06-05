# Ros and SLAM
![[Pasted image 20240605161929.png]]![[Pasted image 20240605161952.png]]
![[Pasted image 20240605162049.png]]
Some SLAM system also want a base footprint frame. Its like a shadow of the base link on the horizontal plane for mapping in 3D

Pose: Position and orientation (Equivalent
to transform frame)
# Setting up the SLAM toolbox
Lets first add the base footprint to `robot_core.xacro`
```xacro
<!-- BASE_FOOTPRINT LINK -->

<joint name="base_footprint_joint" type="fixed">
    <parent link="base_link"/>
    <child link="base_footprint"/>
    <origin xyz="0 0 0" rpy="0 0 0"/>
</joint>

<link name="base_footprint">
</link>
```
Then install the slam toolbox with
```bash
sudo apt install ros-humble-slam-toolbox
```

Were using the online asynchronous mode
-  Online: Working on live data stream
-  Asynchronous: Always processes the most recent scan to avoid lagging
To set this we do the following:
```bash
cp /opt/ros/humble/share/slam_toolbox/config/mapper_params_online_async.yaml dev_ws/src/my_bot/config/
```
(You can press double tab after `params_` to see a list of all the options)
