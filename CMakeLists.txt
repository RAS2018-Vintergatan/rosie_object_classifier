cmake_minimum_required(VERSION 2.8.3)
project(rosie_object_classifier)

find_package(Boost REQUIRED COMPONENTS system filesystem thread)
find_package(catkin REQUIRED COMPONENTS rospy sensor_msgs cv_bridge std_msgs)
find_package(OpenCV REQUIRED)

catkin_python_setup()

catkin_package(
  DEPENDS Boost PCL
  CATKIN_DEPENDS rospy sensor_msgs cv_bridge std_msgs
  LIBRARIES 
)

include_directories(
  include
  ${Boost_INCLUDE_DIRS}
  ${catkin_INCLUDE_DIRS}
)

#link_directories(
#  ${Boost_LIBRARY_DIRS}
#)



#add_executable(rosie_object_classifier src/rosie_object_classifier.py)
#target_link_libraries(rosie_object_classifier ${OpenCV_LIBS} ${catkin_LIBRARIES}  ${Boost_LIBRARIES})
#add_dependencies(rosie_object_classifier sensor_msgs cv_bridge std_msgs)

#Do chmod +x filename.py in the folder containing the file and then do catkin_make

install(PROGRAMS src/rosie_object_classifier DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
