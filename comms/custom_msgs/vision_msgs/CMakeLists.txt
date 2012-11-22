##############################################################################
# CMake
##############################################################################

# set(CMAKE_VERBOSE_MAKEFILE TRUE)

##############################################################################
# Catkin
##############################################################################

project(vision_msgs)

catkin_project(vision_msgs
  INCLUDE_DIRS include
  DEPENDS std_msgs 
)

# Include actionlib_msgs as a dependency if adding actions
# Move this call to stack.xml if you are calling find_package on a particular
# component alot.
find_package(ROS REQUIRED COMPONENTS genmsg std_msgs actionlib_msgs)

include_directories(include)

##############################################################################
# Sources
##############################################################################

#add_message_files(
#  DIRECTORY msg
#  FILES
#  GrabbingObject.msg
#)

add_action_files(
  DIRECTORY action
  FILES 
  FillCupWithWater.action
  GrabbingObject.action
  ObjectDetection.action
  PassingObjectToUser.action
  PuttingObjectOnTray.action
  ReleaseGripper.action
)

# Include actionlib_msgs as a dependency if adding actions
generate_messages(DEPENDENCIES std_msgs std_msgs actionlib_msgs)

##############################################################################
# Install
##############################################################################

install(DIRECTORY include/
        DESTINATION include
        FILES_MATCHING PATTERN "*.h"
        PATTERN ".svn" EXCLUDE
        PATTERN ".git" EXCLUDE)



