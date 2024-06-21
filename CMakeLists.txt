cmake_minimum_required(VERSION 3.8)
project(sensopart_interfaces)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

# declare the message files to generate code for
set(msg_files
  "msg/Job.msg"
)

# declare the service files to generate code for
set(srv_files
  "srv/GetPose.srv"
  "srv/Calibration.srv"
  "srv/ExtendedTrigger.srv"
  "srv/GetImage.srv"
  "srv/GetJobs.srv"
  "srv/SetJob.srv"
  "srv/TriggerRobotics.srv"
)

# declare the action files to generate code for
#set(action_files

#)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
#  ${action_files}
  DEPENDENCIES builtin_interfaces std_msgs sensor_msgs geometry_msgs
)

ament_export_dependencies(rosidl_default_runtime)


ament_package()