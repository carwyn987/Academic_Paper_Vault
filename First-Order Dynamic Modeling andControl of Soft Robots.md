
![[first_order_dynamic_modeling_and_control_of_soft_robots.pdf]]

## Notes / Areas to learn about in Soft Robot Modeling

 - [Constant curvature model](https://www.opencontinuumrobotics.com/101/2022/12/09/tdcr-cc-model.html) - used for modeling tendon-driven continuum robots (very similar to my own AMPER project).![[constant_curvature_model.png]]
   A simple model ("parameters defining the robot configuration") may consist of m "triplets of curvature", i.e. (the angle of the plane containing the arc, the arc length, and the arc curvature (often represented as 1/r)).
 - Cosserat-rods - a generalization of Kirchhoff rods that includes stretching and shearing
 - Kirchhoff rods - a model for 1-d rods that incorporates bending and twisting
 - **Continuum robot** - a type of robot that can change its shape, position, etc. by flexing along its entire length. Usually, this refers to robots with infinite degrees of freedom and infinite joints, made of soft flexible material. This may be similar enough to my serpant-like AMPER robot to model it in this way. Robots of this fashion driven with tendons are called **Tendon-Driven Continuum Robots (TDCR)**.
 - Steady state assumption - key state variables like PVA and rotational speeds are constant.
 - 

Spaces associated with robotics
 - Cartesian Space - generally 3 dimensions with x,y,z dimensions
 - Adding orientation (e.g. Bryant Tait Angles) to the cartesian space gives some unnamed six dimensional space.
 - Operational or Task Space - often this six dimensional space, and is the space in which the robot operates and executes tasks. It seems like this refers only to the end effector - that which is relevant to the task.
 - Joint Space refers to the space that defines all possibilities for joint phases. The dimensionality is the number of degrees of freedom of the robot. The joint space is what you get after solving the inverse kinematics problem from the operation/task space. More than one point in the joint space can have the same operational space configuration.
 - Configuration Space - a subset of the joint space that accounts for self and obstacle collision, and other limitations of the physical robot.

## Theory

 - Full dynamics of a soft robot can be represented using the configuration-space variable as M(q)q̈ + C(q, q̇)q̇ + G(q) = τ, where "M(q) represents the inertial properties, C(q, q̇) combines the coriolis, centrifugal and damping elements, G(q) represents the  gravitational and stiffness effects and τ is the generalized force applied internally by the robot." The second order can often be ignored once q̇ is non-zero once movement begins.
 - "Soft robots typically have high damping values with low inertial properties. This is because they are commonly fabricated with viscoelastic materials with low material density."
 - 
## ToDo
 - "For an alternate approach that introduces a control-oriented modeling of soft robots, the readers are suggested to look into Della Santina and Rus (2019)" [link](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8913522)
 - Piece-wise Constraint Strain (PCS) approach for soft-rigid multibody systems - Renda and Seneviratne (2018)
 - Review standard applications of Jacobians, skew-symmetric, 3D rotation groups (SO3), SE3, lie groups