cmake_minimum_required(VERSION 2.8.3)
project(uvc_cam)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  sensor_msgs
  image_transport
  tf
  camera_info_manager
  dynamic_reconfigure
  driver_base)


generate_dynamic_reconfigure_options(
  cfg/UVCCam.cfg
  )

catkin_package(
  LIBRARIES uvc_cam
  CATKIN_DEPENDS
  roscpp
  sensor_msgs
  image_transport
  tf
  camera_info_manager
  dynamic_reconfigure
  driver_base
  )

include_directories(include)

add_library(uvc_cam src/uvc_cam/uvc_cam.cpp)

add_executable(uvc_cam_node src/uvc_cam_node.cpp)
target_link_libraries(uvc_cam_node uvc_cam ${catkin_LIBRARIES})

