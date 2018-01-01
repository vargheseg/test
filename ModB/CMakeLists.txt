include(${CMAKE_CURRENT_LIST_DIR}/../ModC/CMakeLists.txt)

add_library(ModB b.cpp)
target_link_libraries(ModB 
	PRIVATE
          ModC)
