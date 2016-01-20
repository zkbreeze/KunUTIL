cmake_minimum_required(VERSION 2.8)
project(KunUTIL)
set($ENV{KunUTIL_DIR} "${PROJECT_SOURCE_DIR}")

option(DEBUG "DEBUG" OFF)

if(DEBUG)
	set(CMAKE_BUILD_TYPE "Debug")
	add_definitions(-ggdb3)
	add_definitions(-DKVS_ENABLE_DEBUG)
	add_definitions(-D_DEBUG)
endif()

# KVS Library
set(KVS_DIR $ENV{KVS_DIR})
include_directories( ${KVS_DIR}/include )

# Build Library
file(GLOB_RECURSE  Library "${PROJECT_SOURCE_DIR}/include/*.cpp")
add_library(kunUTIL ${Library})
set_target_properties(kunUTIL PROPERTIES
         ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib)