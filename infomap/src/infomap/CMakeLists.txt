cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(infomapmex)
 
set(INFOMAP_SRCS
	FlowNetwork.cpp 
	InfomapBase.cpp
	InfomapContext.cpp
	MemFlowNetwork.cpp
	MemNetwork.cpp
	MemoryNetworkAdapter.cpp
	MultiplexNetwork.cpp
	Network.cpp
	NetworkAdapter.cpp
	Node.cpp
	TreeData.cpp
	)

set(INFOMAP_HDRS
	Edge.h
	flowData.h
	flowData_traits.h
	FlowNetwork.h
	InfomapBase.h
	InfomapContext.h
	InfomapGreedy.h
	InfomapGreedyCommon.h
	InfomapGreedySpecialized.h
	InfomapGreedyTypeSpecialized.h
	MemFlowNetwork.h
	MemNetwork.h
	MemoryNetworkAdapter.h
	MultiplexNetwork.h
	Network.h
	NetworkAdapter.h
	Node.h
	NodeFactory.h
	TreeData.h
	treeIterators.h
	)

add_library(infomap ${INFOMAP_SRCS} ${INFOMAP_HDRS})
