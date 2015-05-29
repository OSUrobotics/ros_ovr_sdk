cmake_minimum_required(VERSION 2.8.3)
project(OculusSDK)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED)
	
set(OVR_DIR ovr_sdk_linux_0.5.0.1)
set(OVR_OUT_DIR ${PROJECT_SOURCE_DIR}/build)

catkin_package(
	INCLUDE_DIRS ${OVR_OUT_DIR}/include
	LIBRARIES ${OVR_OUT_DIR}/lib/libOVRRT64_0.so.5.0.1
	DEPENDS run
	)

#set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR};${CMAKE_MODULE_PATH}")
set(OculusSDK_DIR ${PROJECT_SOURCE_DIR})

add_custom_target(run ALL DEPENDS LoadOculusSDK)

add_custom_command(
	OUTPUT LoadOculusSDK
#	COMMAND make PREFIX=${OVR_OUT_DIR} clean
	COMMAND make PREFIX=${OVR_OUT_DIR} release
	COMMAND make PREFIX=${OVR_OUT_DIR} install
	WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}/sdk/${OVR_DIR}
	)

# Assigns the appropriate libraries
#set (OculusSDK_LIBRARY_DIRS ${OVR_OUT_DIR}/lib/libOVRRT64_0.so.5.0.1)

# Assigns the appropriate includes
#set (OculusSDK_INCLUDE_DIRS ${OVR_OUT_DIR}/include)

#MESSAGE(INFO ${OculusSDK_INCLUDE_DIRS})

#export(PACKAGE OculusSDK)


