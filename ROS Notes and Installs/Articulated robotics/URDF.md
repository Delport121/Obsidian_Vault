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
