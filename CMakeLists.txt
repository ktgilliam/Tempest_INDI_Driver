# define the project name
project(Tempest_Weather C CXX)
cmake_minimum_required(VERSION 3.10)

include(GNUInstallDirs)

#=================================================================================================#
#========================================= Dependencies  =========================================#
#=================================================================================================#
# add our cmake_modules folder
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/02_CMake_Modules/")


# find our required packages
find_package(INDI REQUIRED)
find_package(Nova REQUIRED)
find_package(ZLIB REQUIRED)
find_package(GSL REQUIRED)

# these will be used to set the version number in config.h and our driver's xml file
set(CDRIVER_VERSION_MAJOR 0)
set(CDRIVER_VERSION_MINOR 1)



# set our include directories to look for header files
include_directories( ${CMAKE_CURRENT_BINARY_DIR})
include_directories( ${CMAKE_CURRENT_SOURCE_DIR})
include_directories( ${INDI_INCLUDE_DIR})
include_directories( ${NOVA_INCLUDE_DIR})
include_directories( ${EV_INCLUDE_DIR})

include(CMakeCommon)

# add_subdirectory(00_Utils)
add_subdirectory(01_Tempest_Driver)




