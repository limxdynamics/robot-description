# Copyright information
#
# © [2024] LimX Dynamics Technology Co., Ltd. All rights reserved.

# Declare the minimum required CMake version
cmake_minimum_required(VERSION 3.10)

# Declare the project
project(robot_description)

if($ENV{ROS_VERSION} EQUAL 1)
  # In ROS1 compilation environment
  message("Currently in ROS1 compilation environment")
  catkin_package(CATKIN_DEPENDS)

  # Install directories 'meshes' and 'urdf' to the package share directory
  install(DIRECTORY pointfoot DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
elseif($ENV{ROS_VERSION} EQUAL 2)
  # In ROS2 compilation environment
  message("Currently in ROS2 compilation environment")

  find_package(ament_cmake REQUIRED)

  install(DIRECTORY pointfoot DESTINATION share/${PROJECT_NAME})

  ament_package()
endif()