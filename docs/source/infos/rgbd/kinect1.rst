Kinect1
=======================================
.. image:: /_static/kinect1.jpg
    :width: 250px
    :align: center

.. tip:: The Microsoft Kinect is not available anymore.

Description
-----------

The Kinect is the most famous RGBD sensor.
But it is not available anymore for sale as Microsoft released a new version,
the `Kinect v2 <kinect2.html>`_ also known as "Kinect for Xbox One".

.. image:: /_static/kinect1_inside.png
    :width: 250px
    :align: right

This RGBD sensor contains:
  - a 640x480 RGB camera
  - an infrared emitter
  - a 640x480 depth camera
  - a tilt motor
  - a microphone

The infrared emitter uses a technology called the projected lights that are then
computed to create the depth image.

.. warning:: If you point two kinects to the same surface you won't be able to see correctly on the depth images as the two differents lights will cancel each other

On ROS
------
To run the Kinect1 on ROS, you need to use the `freenect_launch <http://wiki.ros.org/freenect_launch>`_ package
