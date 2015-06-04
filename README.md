# ros_ovr_sdk

A ROS package which builds the Oculus SDK as a shared library and outputs a link to the appropriate includes/libraries that other packages can use.

This library is designed to be upgrade friendly, allowing newer versions of the SDK to be added.

To test the Rift, just type:

     rosrun ros_ovr_sdk OculusWorldDemo
     
To run ovrd, enter the command:

     rosrun ros_ovr_sdk ovrd

See [the Wiki](https://github.com/OSUrobotics/ros_ovr_sdk/wiki) for more details.
