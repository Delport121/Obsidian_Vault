- Unified robot description format

Concepts:
- Link
- Joints
- Parent link and childs
	- Each link can have one parent but many children

Common joint types:
- Revolute: Rotational with fixed limits
- Continues: Continuers rotational
- Prismatic: Linear translational
- Fixed:
- Others

URDF is base on XML:
Series of tags nested in each other

Root tag for URDF -> Robot

Three main characteristics for each link:
- visual 
	- geometry
	- origin
	- material
- collision
	- geometry
	- origin
- inertial
	- mass 
	- origin
	- inertia

# Joint structure
- name 
- type
- parent
- child
- origin
- axis
- limit

Some other tages:
material 
gazebo
transition

- Ros naming convention

# Xacro
-Its a tag that you add to the file

To run the example:


# Testing the example
Clone the repo:
```bash
https://github.com/joshnewans/urdf_example.git
```

One cloned, it has to be build. This can be done in the folder that was created

Once the thing is build, you either have to be in the directory and source it or the directory can be set in the source file.

The refer to the read me for the remaining instructions: (Here are some of the commands used for reference);
```bash
ros2 launch urdf_example rsp.launch.py
ros2 run joint_state_publisher_gui joint_state_publisher_gui
rviz2
```