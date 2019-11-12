cmake_minimum_required (VERSION 2.8.8)
project (test)

add_definitions(-std=c++11)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

SET(CMAKE_INCLUDE_SYSTEM_FLAG_C "-I")
SET( CMAKE_INCLUDE_SYSTEM_FLAG_CXX "-I" CACHE STRING "" FORCE )

find_package(Protobuf REQUIRED)
message(STATUS "Found Protobuf ${PROTOBUF_INCLUDE_DIR} ${PROTOBUF_LIBRARIES}")
include_directories(${PROTOBUF_INCLUDE_DIR})
link_directories(${PROTOBUF_LIB_DIR})

SET(BST_LIB_INSTALL_PATH ./lib)

add_subdirectory(proto)
 
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=c++11 -W")

#find_package( OpenCV REQUIRED )

include_directories(${PROJECT_BINARY_DIR}/proto)

#aux_source_directory(./src DIR_SRCS)

#link_directories(./lib)

set(EXTRA_LIBS
    glog
    gflags
bst_image_proto
    protobuf
    cyber
    )

#include_directories(
#/usr/local/include/eigen3
#/home/toolCode/tensorflow1.8/tensorflow/tensorflow/contrib/makefile/gen/protobuf/include
#) 

add_executable(test  ./src/main.cpp )

#target_link_libraries(test  ${EXTRA_LIBS} ${PROJECT_SOURCE_DIR}/lib/libbst_image_proto.so)
#target_link_libraries(test  cyber bst_image_proto glog gflags protobuf )
target_link_libraries(test cyber cyber_proto fastrtps glog protobuf bst_image_proto gflags)

