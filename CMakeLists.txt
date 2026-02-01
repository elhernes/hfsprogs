cmake_minimum_required(VERSION 3.10)
project(hfsprogs VERSION 1.0 LANGUAGES C)

# This project is a Linux port of Apple's HFS tools
# On macOS, use Apple's native tools instead
if(NOT CMAKE_SYSTEM_NAME STREQUAL "Linux")
    message(FATAL_ERROR "hfsprogs is designed for Linux only. On macOS, use Apple's native HFS tools.")
endif()

# Common compile definitions
add_compile_definitions(
    DEBUG_BUILD=0
    _FILE_OFFSET_BITS=64
    LINUX=1
    BSD=1
)

# Common include directory
include_directories(${CMAKE_SOURCE_DIR}/include)

# Common compiler flags
add_compile_options(-Wall)

# Subdirectories
add_subdirectory(newfs_hfs)
add_subdirectory(fsck_hfs)

# Installation
include(GNUInstallDirs)
