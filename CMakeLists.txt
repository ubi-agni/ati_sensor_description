cmake_minimum_required(VERSION 2.8.3)
project(ati_sensor_description)

find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
)

foreach(dir urdf meshes robots)
   install(DIRECTORY ${dir}/
      DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)
