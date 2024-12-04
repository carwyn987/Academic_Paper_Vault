#Self-Modeling #Robotics 

*The paper provides a method for learning a self-model. The approach uses multi-view depth sensors to capture ground truth data for the model. Then, a neural network consisting of modular kinematic and coordinate feature components learns via space occupancy querying. This approach provides the foundation for various motion planning tasks. Furthermore, the low memory (~1.1MB) and training resources required (<5s 2080ti) make this viable for on-device training.* 

# Notes

The paper captures morphology and forward kinematics in modular neural components, with semantic unstructured knowledge of the kinematics. It learns based off of space occupancy querying.

No explicit mesh, point cloud, or grid representation of 3d self-model. Rather, learns the mapping f: (joint angles, spatial point) -> occupied?

Enjoyed reading the Damage Identification and Recovery section.

## Nitpicks:

"In the real-world experiments, we noticed that the point cloud fusion was very noisy due to imprecise depth information introduced by internal sensor errors, noisy camera calibrations, and importantly, very sparse view points ... The gap of the ground truth data quality between the simulation and real world suggests that the final results in the real-world setup can be greatly improved with better future 3D scanning techniques."

I would imagine that research at this tier would explore the possibility of this improvement. Perhaps this is where industry work branches off from academic work in search of ultimately reliable processes for implementation? Perhaps it is more challenging than I realize. I'm under the assumption that a rig with satisfactory resolution, low noise, and high precision is not prohibitively expensive. 

-> After skimming the paper, they use 5 Intel RealSense D435i RGB-D Camera's with built in IMU's. These are not high-fidelity components, with <2% error at 2 meters away (from specsheet). I'm surprised they didn't use a single higher-precision camera on a turntable for data collection to enable more dense viewpoint sampling, despite longer collection times.
-> This is covered in the discussion, where they cite cost, time, and labor as reasons for not improving sensor performance. Fair enough.

## Research Further (for me)

 - '"see in our minds eye" (14)'
 - "Tessellated trangle meshes"
 - "Voxelized occupancy grids"
 - "SIREN network"
 - "zero-level set Signed Distance Function (SDF)"
 - "Eikonal boundary value problem"
 - "RRT* (18)"
 - PyBullet vs Gymnasium vs IsaacGym(Lab)

## Extension Ideas

I wonder if this idea of self-modeling could be extended to predict force, and without the depth sensors. For example, if we had a cube with a built in high precision IMU / tracking, with dense grids of force sensors on all faces, I wonder if we could model effectors of robots, with force (i.e. beyond simply visual models). The robot would begin exploring, occasionally touching the cube providing a datapoint to the model. Once the manipulator learned to pick up the cube, it would begin to learn the applied force (beyond the self-modelling presented in this paper), and it would learn the extent of the movement of the effector.

![[full_body_visual_self-modeling_of_robot_morphologies.pdf]]