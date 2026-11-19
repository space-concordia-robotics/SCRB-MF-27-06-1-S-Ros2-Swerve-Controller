cmake_minimum_required(VERSION 3.22)
project(swerve_simulation)

# No C/C++ targets in this package; reference CMAKE_EXPORT_COMPILE_COMMANDS so
# passing it globally to colcon build does not emit an unused-variable warning.
if (CMAKE_EXPORT_COMPILE_COMMANDS)
endif ()

find_package(ament_cmake REQUIRED)

install(
        DIRECTORY config launch urdf worlds
        DESTINATION share/${PROJECT_NAME}/
)

ament_package()
