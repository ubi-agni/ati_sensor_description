cmake_minimum_required(VERSION 2.8.3)
project(ati_sensor_description)

find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
)

catkin_package()

install(DIRECTORY robots meshes urdf
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
