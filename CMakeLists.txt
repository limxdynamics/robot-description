# Copyright information
#
# © [2024] LimX Dynamics Technology Co., Ltd. All rights reserved.

# Declare the minimum required CMake version
cmake_minimum_required(VERSION 3.10)

# Declare the project
project(robot_description)

# Declare the catkin package
catkin_package(
  CATKIN_DEPENDS
)

# Install directories 'meshes' and 'urdf' to the package share directory
install(DIRECTORY pointfoot DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
