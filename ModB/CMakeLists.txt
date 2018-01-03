add_library(ModB b.cc)
target_include_directories(ModB 
	PUBLIC 
	  public_includes)
target_link_libraries(ModB PRIVATE ModC)
