cmake_minimum_required(VERSION 3.14)

project(MyProject)

add_subdirectory(.. ${CMAKE_BINARY_DIR}/GroupSourcesByFolder)

# Absolute file paths
FILE(GLOB_RECURSE headers "${CMAKE_CURRENT_SOURCE_DIR}/*.h")
FILE(GLOB_RECURSE sources "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")

add_library(MyLibraryA ${headers} ${sources})

GroupSourcesByFolder(MyLibraryA)

# Relative file paths
set(headers
    include/lib.h
    source/a/lib.h
    source/b/lib.h
    source/c/lib.h)
set(sources
    source/a/source.cpp
    source/b/source.cpp
    source/c/source.cpp)
    
add_library(MyLibraryB ${headers} ${sources})

GroupSourcesByFolder(MyLibraryB)
