# Swerve Drive

The packages in this folder are used for implementing swerve drive.

Packages:

- swerve-controller: implements the ros2_control controller interface for swerve drive.
- swerve-simulation: simple simulation for testing swerve drive


# Setup
## 0. Build
```bash
source /opt/ros/jazzy/setup.bash
colcon build --packages-up-to swerve_controller swerve_simulation --cmake-args -DCMAKE_C_COMPILER=gcc -DCMAKE_CXX_COMPILER=g++ -DCMAKE_BUILD_TYPE=Release
```

## 1. T1: Launch the Swerve Sim
```bash
source /opt/ros/jazzy/setup.bash
source install/setup.bash
ros2 launch swerve_simulation sim.launch.py
```

# 2. Terminal 2: Start Teleop

### Keyboard Teleop
```bash
source /opt/ros/jazzy/setup.bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -p stamped:=true -p use_sim_time:=true -r cmd_vel:=/swerve_controller/cmd_vel
```