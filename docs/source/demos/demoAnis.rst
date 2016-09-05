Demo Anis
=========

Publish the robot in ROS
------------------------
The joints of the robot should be published in /joint_states
If no robot_publisher is running, just use this launch file:

.. code-block:: bash

  roslaunch lwr_utils lwr.launch load_table:=true load_base:=true load_handle:=true

Run the Kinects
---------------
**On kuka-demo@kuka-viz2 (mdp: kukademo)**


Here you will run the Kinect v2  placed on the wall called kinectV2
Use  mux kinectV2_processing and all the necessary things to run should appear right in front of you. Just run all of them in any order.
 If not here is the list of what you need to run:

.. code-block:: bash

  roslaunch kinects_human_tracking kinectV2.launch publish_tf:=true base_name:=kinectV2
  roslaunch kinects_human_tracking kinectV2_extrinsics.launch
  roslaunch kinects_human_tracking kinect_img_bg_store_kinectV2.launch kinect_name:=kinectV2
  roslaunch kinects_human_tracking kinect_img_bg_sub_kinectV2.launch kinect_name:=kinectV2
  roslaunch realtime_urdf_filter filter_kinectV2.launch kinect_name:=kinectV2
  roslaunch realtime_urdf_filter create_pc_kinectV2.launch kinect_name:=kinectV2

**On kukademo@kuka-viz (mdp: kukademo)**

Here you will run the Xtions.
The one in the corner of the robot's cage is kinect1
The second in the ceiling is kinect2
Like on kuka-viz2 you can use mux:

.. code-block:: bash

  mux kinect1_processing
  mux kinect2_processing

Which is equivalent to

.. code-block:: bash

  roslaunch kinects_human_tracking kinect1.launch
  roslaunch kinects_human_tracking kinect1_extrinsics.launch
  roslaunch kinects_human_tracking kinect_img_bg_store.launch kinect_name:=kinect1
  roslaunch kinects_human_tracking kinect_img_bg_sub.launch kinect_name:=kinect1
  roslaunch realtime_urdf_filter filter.launch kinect_name:=kinect1
  roslaunch realtime_urdf_filter create_pc.launch kinect_name:=kinect1

Run the tracking
---------------
**On kuka-viz or kuka-viz2**

Last step is to merge the kinects and run tracking mux kinect_tracking
Just fill in topic_name1 for using only one Kinect
Fill in topic_name2 and topic_name3 if you want to merge 2 or 3 kinects
It is equivalent to:

.. code-block:: bash

  roslaunch kinects_human_tracking kinect_merge.launch  topic_name1:=/kinectV2/depth_registered/downsampled_filtered_points topic_name2:=/kinect1/depth_registered/downsampled_filtered_points topic_name3:=/kinect2/depth_registered/downsampled_filtered_points
  roslaunch kinects_human_tracking closest_pt_tracking.launch
