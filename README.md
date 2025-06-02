# Vectornav ROS2 Driver

A ROS2 node for VectorNav INS / GNSS devices. 

This package that provides both raw and sensor_msg interfaces for the VN100, 200, & 300 devices. 
It has been entirely redesigned from the ROS1 package to provide a good basis to build into applications
without requiring modification of the node itself. The majority of the device configuration settings are 
exposed as ROS2 parameters that can be modified from a launch file. 


## QuickStart

Pre-build (Zoe)

1. Set up permissions for access to /dev/ttyUSB* devices (change username from zoe2 as needed): `sudo adduser zoe2 dialout`
2. Restart computer
3. Check setup (change baud rate and port as needed): `picocom -b 921600 /dev/ttyUSB0`

Build

4. `git clone https://github.com/PlanetaryRobotics/vectornav.git -b ros2`
5. `cd vectornav` 
6. `colcon build`

Run with ros2 run (Option 1)

7. (Terminal 1) `ros2 run vectornav vectornav`
8. (Terminal 2) `ros2 topic echo /vectornav/raw/common`
9. (Terminal 3) `ros2 run vectornav vn_sensor_msgs`
10. (Terminal 4) `ros2 topic echo /vectornav/imu`

Run with ros2 launch (Option 2, uses parameters from `vectornav.yaml`)

11. (Terminal 1) `ros2 launch vectornav vectornav.launch.py`
12. (Terminal 2) `ros2 topic echo /vectornav/raw/common`
13. (Terminal 3) `ros2 topic echo /vectornav/imu`

## vectornav node

This node provides a ROS2 interface for a vectornav device. It can be configured
via ROS parameters and publishes sensor data via custom ROS topics as close to raw as possible.


## vn_sensor_msgs node

This node will convert the custom raw data topics into ROS2 sensor_msgs topics to make it easier 
to integrate with other ROS2 packages. 


## References 

[1] [VectorNav](http://www.vectornav.com/)
