include(${CMAKE_CURRENT_LIST_DIR}/../ModC/CMakeLists.txt)
add_library(ModA  $CMAKE_CURRENT_LIST_DIR}/a.cpp)
target_link_libraries(ModA
	PRIVATE
	  ModC)
