# SCRB-MF-27-06-1-S-Ros2-Swerve-Controller
Repository for the development of the drive train ROS2 control controller. This includes the custom swerve drive, Ackermann and differential drive controllers.

## Current Goal:
Currently we are implementing a Swerve Drive (specifically Four-Wheel Independent Steering / 4WIS). 
The current tasks can be found in [TODO.md](swerve-drive/TODO.md)

## Overal Project Structure
```mermaid
graph TD;
  joy_input["`Any Joystick
  Hardware`"]
  joy_node["`Joy_Node`"]
  joy["`/joy
  sensor_msgs/msg/Joy`"]
  controller_config["`Configuration File
  for Connected Controller`"]
  joy_demux["`joy_demux_node`"]
  cmd_vel["`/cmd_vel
  geometry_msgs/msg/TwistStamped`"]
  controller["`Drive Train Controllers
  ros2_control Controller`"]
  interface["`State and Command Interfaces
  ros2_control Hardware Interface`"]
  can["`CAN Frames
  Controller Area Network Communication Protocol`"]
  sensors[Sensor Data]
  actuators[Actuator Command]

  controller_config --> joy_demux
  joy_input --> joy_node
  joy_node --> joy
  joy --> joy_demux
  
  joy_demux --> cmd_vel
  cmd_vel --> controller
  controller <--> interface
  interface <--> can
  can --> actuators
  sensors --> can
```

## Extra controllers to implement in the future:

### All ready existing controllers to implement:
- Differential Drive Controller
- Ackermann Steering Controller

### Custom controllers to implement:
- Double Ackermann Steering Controller