##############################################################################
# CMake
##############################################################################

cmake_minimum_required(VERSION 3.0.2)
project(rosjava_core)

##############################################################################
# Catkin
##############################################################################

find_package(catkin REQUIRED 
    rosjava_build_tools
    geometry_msgs
    nav_msgs
    rosjava_test_msgs
    rosgraph_msgs
    sensor_msgs
    tf2_msgs
)

catkin_rosjava_setup(publish installDist)

# make sure messages get built first if genjava is enabled
add_dependencies(gradle-${PROJECT_NAME} ${catkin_EXPORTED_TARGETS})

catkin_package()

##############################################################################
# Installation
##############################################################################

install(DIRECTORY ${ROS_MAVEN_DEPLOYMENT_REPOSITORY}/org/ros/rosjava_core/
        DESTINATION ${CATKIN_GLOBAL_MAVEN_DESTINATION}/org/ros/rosjava_core)
