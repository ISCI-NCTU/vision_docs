Demo PegInHole
=======================================

Moveit
------
Moveit will update the planning scene with the objects in the environment

.. code-block:: bash

  roslaunch lwr_moveit_config run.launch moveit_rviz:=false

Camera
------
The camera mounted on the robot. Green and orange lights on it should be lightened up

.. code-block:: bash

  roslaunch lwr_peg_in_hole kuka_cam.launch

AR tags
-------
This node will looks for the tags in the camera images to locate the parts

.. code-block:: bash

  roslaunch lwr_peg_in_hole find_objects_w_tags.launch

Services
--------
You will need a couple of services to be able to run the demo script.

.. code-block:: bash

  rosrun lwr_peg_in_hole update_scene_service       #update object in scene
  rosrun lwr_peg_in_hole estimate_holes_service     #estimate the holes pose
  rosrun lwr_peg_in_hole find_hole_pose_service     #look for the exact hole pose


Action servers
--------------
This action server is used to (un)screw the fastener with the screwdriver

.. code-block:: bash

  rosrun lwr_peg_in_hole screwdriver_action_server

Start the demo
--------------
A script to run the demo

.. code-block:: bash

  rosrun lwr_peg_in_hole real_demo_test0

For now this script does the following:

- Wait for the different service nodes and action servers to be ready
- Wait for a press to ENTER !
- Move to start
- Move to first look up pose
- Update the pose of the object in the MoveIt planning scene
- Load the position of the holes
- Go above the first hole (approximatively...)
- Go down a little bit
- Look for the exact hole pose with the estimate
- Go above the exact hole pose
