cmake_minimum_required(VERSION 2.8.3)
project(medicbot_controller)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  joy
)

catkin_package()

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(medicbot_teleop_joy src/medicbot_teleop_joy.cpp)

target_link_libraries(medicbot_teleop_joy
  ${catkin_LIBRARIES}
)
