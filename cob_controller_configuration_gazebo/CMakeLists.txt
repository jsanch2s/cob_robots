# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(cob_controller_configuration_gazebo)

# rostest for robots
SET(robotlist
cob3-1
cob3-2
cob3-3
cob3-4
cob3-5
cob3-6
cob3-7
raw3-1
raw3-2
raw3-3
raw3-4
raw3-5
raw3-6
desire
)

# loop through list of robots for testing
FOREACH(robot ${robotlist})
	MESSAGE("testing for robot: ${robot}")
	#rosbuild_add_roslaunch_check(ros/launch/default_controllers_${robot}.launch robot:=${robot})
ENDFOREACH(robot)

catkin_package(
    DEPENDS rostopic joint_trajectory_action cob_bringup cob_sick_s300 cob_relayboard cob_sound image_proc schunk_simulated_tactile_sensors cob_phidgets
 )


## Mark cpp header files for installation
install(DIRECTORY ros/launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/ros/launch
)

install(DIRECTORY ros/controller/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/ros/controller
)

install(PROGRAMS ros/src/fake_diagnostics.py ros/src/gazebo_services.py
  DESTINATION ${CATKIN_PACKAGE_PYTHON_DESTINATION}
)
