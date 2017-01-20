cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(infomapmex)
set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake")
set(PROJECT_BINARY_DIR "${CMAKE_CURRENT_SOURCE_DIR}/build/")
set(LIBRARY_OUTPUT_PATH "${CMAKE_CURRENT_SOURCE_DIR}/build/" CACHE PATH "Single directory for all libraries")
set(EXECUTABLE_OUTPUT_PATH "${CMAKE_CURRENT_SOURCE_DIR}/build/" CACHE PATH "Single directory for all executables")


# Check for the support of C++11 compliant compilers
include(CheckCXXCompilerFlag)
CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
if(COMPILER_SUPPORTS_CXX11)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
elseif(COMPILER_SUPPORTS_CXX0X)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
else()
        message(FATAL_ERROR "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
endif()

set(CMAKE_CXX_FLAGS "-Wall -Wno-deprecated-register -Wno-deprecated-declarations -std=c++11 ${CMAKE_CXX_FLAGS}")

# Specify if matlab support and python wrappers are to be compiled. Default OFF
# MATLAB support needs MEX (Tested on Ubuntu 14.04, Matlab R2013a)
option(MATLAB_SUPPORT "Mex with MATLAB" OFF)
option(OCTAVE_SUPPORT "Oct with Octave mkoctfile" OFF)
option(COMPILE_TESTS "Compile all debugging tests" OFF)

if (OPENMP_SUPPORT)
    find_package(OpenMP)
    if (OPENMP_FOUND)
        set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
        set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
    endif()
endif (OPENMP_SUPPORT)

# To enable infomap namespace and avoid confusion
add_definitions("-DNS_INFOMAP")
add_definitions("-DAS_LIB")

if(MATLAB_SUPPORT)
    find_package(MyMatlab)
    message(STATUS "Matlab include directories: ${MATLAB_INCLUDE_DIRS}")
    include_directories(${MATLAB_INCLUDE_DIRS})
    if (MATLAB_NOT_FOUND)
        message(FATAL "Error matlab not found")
    endif()
    add_definitions("-DMATLAB_SUPPORT")
endif()

if(OCTAVE_SUPPORT)
    find_package(OCTAVE)
    include_directories(${OCTAVE_INCLUDE_DIRS})
    add_definitions("-DOCTAVE_SUPPORT")
endif(OCTAVE_SUPPORT)

find_package(IGraph)
include_directories(${IGRAPH_INCLUDES})

# Add the subdirectory with the source code of infomap
add_subdirectory(infomap)
# Add the subdirectory with the matlab mex wrapper
add_subdirectory(src)
