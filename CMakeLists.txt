cmake_minimum_required(VERSION 3.0)
project(test_project)

add_subdirectory(ModA)
add_subdirectory(ModB)
add_subdirectory(ModC)

add_executable(main main.cpp)
target_link_libraries(main 
	PRIVATE 
	  ModA ModB)

