cmake_minimum_required(VERSION 2.8.3)
project(OculusSDK)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED)

set(OVR_DIR ovr_sdk_linux_0.5.0.1)

add_custom_target(run ALL DEPENDS LoadOculusSDK)
add_custom_command(
	OUTPUT LoadOculusSDK
	COMMAND make PREFIX=${PROJECT_SOURCE_DIR} release
	COMMAND make PREFIX=${PROJECT_SOURCE_DIR} install
	WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
	)

# Assigns the appropriate libraries
set (OculusSDK_LIBRARY_DIRS ${PROJECT_SOURCE_DIR}/lib)

# Assigns the appropriate includes
set (OculusSDK_INCLUDE_DIRS ${PROJECT_SOURCE_DIR}/include)

