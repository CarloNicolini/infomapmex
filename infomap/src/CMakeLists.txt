cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(infomapmex)
 
set(INFOMAP_SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR})

include_directories(${INFOMAP_SRC_DIR})
include_directories(${INFOMAP_SRC_DIR}/infomap)
include_directories(${INFOMAP_SRC_DIR}/utils)
include_directories(${INFOMAP_SRC_DIR}/io)

set(INFOMAP_SRCS
	${INFOMAP_SRC_DIR}/Infomap-igraph-interface.cpp
        ${INFOMAP_SRC_DIR}/Infomap.cpp
	${INFOMAP_SRC_DIR}/infomap/FlowNetwork.cpp
	${INFOMAP_SRC_DIR}/infomap/InfomapBase.cpp
	${INFOMAP_SRC_DIR}/infomap/InfomapContext.cpp
	${INFOMAP_SRC_DIR}/infomap/MemFlowNetwork.cpp
	${INFOMAP_SRC_DIR}/infomap/MemNetwork.cpp
	${INFOMAP_SRC_DIR}/infomap/MemoryNetworkAdapter.cpp
	${INFOMAP_SRC_DIR}/infomap/MultiplexNetwork.cpp
	${INFOMAP_SRC_DIR}/infomap/Network.cpp
	${INFOMAP_SRC_DIR}/infomap/NetworkAdapter.cpp
	${INFOMAP_SRC_DIR}/infomap/Node.cpp
	${INFOMAP_SRC_DIR}/infomap/TreeData.cpp
	#${INFOMAP_SRC_DIR}/Informatter.cpp
	${INFOMAP_SRC_DIR}/io/BipartiteClusterReader.cpp
	${INFOMAP_SRC_DIR}/io/ClusterReader.cpp
	${INFOMAP_SRC_DIR}/io/HierarchicalNetwork.cpp
	${INFOMAP_SRC_DIR}/io/ProgramInterface.cpp
	${INFOMAP_SRC_DIR}/io/TreeDataWriter.cpp
	${INFOMAP_SRC_DIR}/io/version.cpp
	${INFOMAP_SRC_DIR}/utils/FileURI.cpp
	${INFOMAP_SRC_DIR}/utils/Logger.cpp
    )

set(INFOMAP_HDRS
	${INFOMAP_SRC_DIR}/Infomap-igraph-interface.h
        ${INFOMAP_SRC_DIR}/Infomap.h
	${INFOMAP_SRC_DIR}/infomap/Edge.h
	${INFOMAP_SRC_DIR}/infomap/flowData.h
	${INFOMAP_SRC_DIR}/infomap/flowData_traits.h
	${INFOMAP_SRC_DIR}/infomap/FlowNetwork.h
	${INFOMAP_SRC_DIR}/infomap/InfomapBase.h
	${INFOMAP_SRC_DIR}/infomap/InfomapContext.h
	${INFOMAP_SRC_DIR}/infomap/InfomapGreedy.h
	${INFOMAP_SRC_DIR}/infomap/InfomapGreedyCommon.h
	${INFOMAP_SRC_DIR}/infomap/InfomapGreedySpecialized.h
	${INFOMAP_SRC_DIR}/infomap/InfomapGreedyTypeSpecialized.h
	${INFOMAP_SRC_DIR}/infomap/MemFlowNetwork.h
	${INFOMAP_SRC_DIR}/infomap/MemNetwork.h
	${INFOMAP_SRC_DIR}/infomap/MemoryNetworkAdapter.h
	${INFOMAP_SRC_DIR}/infomap/MultiplexNetwork.h
	${INFOMAP_SRC_DIR}/infomap/Network.h
	${INFOMAP_SRC_DIR}/infomap/NetworkAdapter.h
	${INFOMAP_SRC_DIR}/infomap/Node.h
	${INFOMAP_SRC_DIR}/infomap/NodeFactory.h
	${INFOMAP_SRC_DIR}/infomap/TreeData.h
	${INFOMAP_SRC_DIR}/infomap/treeIterators.h
	${INFOMAP_SRC_DIR}/io/BipartiteClusterReader.h
	${INFOMAP_SRC_DIR}/io/ClusterReader.h
	${INFOMAP_SRC_DIR}/io/Config.h
	${INFOMAP_SRC_DIR}/io/convert.h
	${INFOMAP_SRC_DIR}/io/HierarchicalNetwork.h
	${INFOMAP_SRC_DIR}/io/ProgramInterface.h
	${INFOMAP_SRC_DIR}/io/SafeFile.h
	${INFOMAP_SRC_DIR}/io/TreeDataWriter.h
	${INFOMAP_SRC_DIR}/io/version.h
	${INFOMAP_SRC_DIR}/utils/Date.h
	${INFOMAP_SRC_DIR}/utils/FileURI.h
	${INFOMAP_SRC_DIR}/utils/gap_iterator.h
	${INFOMAP_SRC_DIR}/utils/infomath.h
	${INFOMAP_SRC_DIR}/utils/Logger.h
	${INFOMAP_SRC_DIR}/utils/MersenneTwister.h
	${INFOMAP_SRC_DIR}/utils/Stopwatch.h
	${INFOMAP_SRC_DIR}/utils/types.h
    )

add_library(infomap SHARED ${INFOMAP_SRCS} ${INFOMAP_HDRS})
#add_executable(infomap ${INFOMAP_SRC_DIR}/Infomap.cpp )
