# Copyright information
#
# © [2024] LimX Dynamics Technology Co., Ltd. All rights reserved.

# Declare the minimum required CMake version
cmake_minimum_required(VERSION 3.10)

# Declare the project
project(robot_description)

if(DEFINED ENV{ROS_VERSION})
  if($ENV{ROS_VERSION} EQUAL 1)
    # In ROS1 compilation environment
    message("Currently in ROS1 compilation environment")

    find_package(catkin REQUIRED COMPONENTS roscpp)
    
    catkin_package(CATKIN_DEPENDS)

    # Install directories 'meshes' and 'urdf' to the package share directory
    install(DIRECTORY pointfoot wheellegged DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
  elseif($ENV{ROS_VERSION} EQUAL 2)
    # In ROS2 compilation environment
    message("Currently in ROS2 compilation environment")

    find_package(ament_cmake REQUIRED)

    install(DIRECTORY pointfoot wheellegged DESTINATION share/${PROJECT_NAME})

    ament_package()
  else()
    message(WARNING "Unknown ROS version: ${ROS_VERSION}")
  endif()
else()
  if(DEFINED ENV{AMENT_PREFIX_PATH})
    message("Currently is not in ROS compilation environment")
    find_package(ament_cmake REQUIRED)
    install(DIRECTORY pointfoot wheellegged DESTINATION etc/${PROJECT_NAME})
    ament_package()
  endif()
endif()