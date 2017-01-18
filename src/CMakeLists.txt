cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(infomapmex)

include_directories(eigen)
add_mex(infomapmx infomapmex.cpp Graph.cpp igraph_utils.cpp)
target_link_libraries(infomapmx infomap ${MATLAB_LIBRARIES} ${IGRAPH_LIBRARIES})
