cmake_minimum_required(VERSION 2.8.3)
project(fcm_control)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
roscpp
  rospy
  std_msgs
  controller_manager
  message_generation
)



## Generate services in the 'srv' folder
add_service_files(
   FILES
   x_joint_cmd.srv
 )


## Generate added messages and services with any dependencies listed here
generate_messages(
   DEPENDENCIES
   std_msgs
)


###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES fcm_control
#  CATKIN_DEPENDS roscpp rospy std_msgs
#  DEPENDS system_lib
   CATKIN_DEPENDS message_runtime
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
# include_directories(incluce)
include_directories(
  ${catkin_INCLUDE_DIRS}
)
add_executable(control_manager src/control_manager.cpp)
add_executable(x_joint_cmd_server src/x_joint_cmd_server.cpp)

target_link_libraries(control_manager ${catkin_LIBRARIES})
target_link_libraries(x_joint_cmd_server ${catkin_LIBRARIES})
