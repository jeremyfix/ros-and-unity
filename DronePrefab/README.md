
[![A drone in unity](https://raw.githubusercontent.com/jeremyfix/ros-and-unity/master/DronePrefab/media/drone_unity.png)](https://youtu.be/7dAWG5NHZac)


The drone mesh is the one provided by tum-simulator[1], in particular, the quadrotor meshes in the cvg_sim_gazebo directory. The URDF file has been imported with the URDFImporter of ros-sharp [2]


The control is very naïve. It's using a PID controller with absolutely no knowledge about the true dynamics of the drone. It is just regulating the forces of the propellers in order to minimize an error. Four PID controllers are used :
1) for the altitude, which seeks to minimize an error in position, with a target moving at a desired velocity. It provides a force to the propellers
2) for the pitch, roll : which seek to minimize an error in velocity. It provides a force to the propellers
3) for the yaw which seek to minimize an error in angular velocity. It provides a torque on the object.

A third person camera is tracking the drone from behind.

The drone is equiped with a camera which can be stabilized, i.e. compensate for the pitch and roll of the drone in order to stay horizontal.

If you want to test the drone, take an empty scene, drag and drop the Drone prefab. Then create an empty object and add the "KeyToCmdVel" script. You can then move the drone with the up/down/left/right arrows, pageup/pagedown and w/x for the yaw.

[1] https://github.com/tum-vision/tum_simulator

[2] https://github.com/siemens/ros-sharp/
