cmake_minimum_required(VERSION 2.6)

project(tinygles)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

link_directories(${CMAKE_BINARY_DIR}/lib /usr/X11R6/lib)
add_definitions(-g -std=gnu99 -O2 -ffast-math)
if(CMAKE_SYSTEM_PROCESSOR MATCHES "^arm")
    add_definitions(-fsingle-precision-constant -mfpu=neon -march=armv7-a -mcpu=cortex-a8 -mtune=cortex-a8)
endif()
include_directories(include)
add_subdirectory(src)
