cmake_minimum_required(VERSION 3.0)
project(test_project)

include(${CMAKE_CURRENT_LIST_DIR}/ModA/CMakeLists.txt)
include(${CMAKE_CURRENT_LIST_DIR}/ModB/CMakeLists.txt)

add_executable(main main.cpp)
target_link_libraries(main 
	PRIVATE 
	  ModA ModB)

