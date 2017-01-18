cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(infomapmex)

include_directories(eigen)
include_directories(${CMAKE_SOURCE_DIR}/infomap/src/)
add_mex(infomapmx infomapmex.cpp)
target_link_libraries(infomapmx infomap ${MATLAB_LIBRARIES} ${IGRAPH_LIBRARIES})
