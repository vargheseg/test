add_library(ModA  a.cc)
target_include_directories(ModA 
	PUBLIC
	  public_includes)
target_link_libraries(ModA PRIVATE ModC)
