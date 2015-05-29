cmake_minimum_required(VERSION 2.8.3)
project(OculusSDK)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED)
	
set(OVR_DIR ovr_sdk_linux_0.5.0.1)
set(OVR_OUT_DIR ${PROJECT_SOURCE_DIR}/build)

set(OculusSDK_DIR ${PROJECT_SOURCE_DIR})

# Make must be executed first, when the dependency is located.

execute_process(
	COMMAND make PREFIX=${OVR_OUT_DIR} release
	COMMAND make PREFIX=${OVR_OUT_DIR} install
	WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}/sdk/${OVR_DIR}
	)

catkin_package(
	INCLUDE_DIRS ${OVR_OUT_DIR}/include
	LIBRARIES ${OVR_OUT_DIR}/lib/libOVRRT64_0.so.5.0.1
	DEPENDS run
	)
