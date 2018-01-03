This repo was created to go with the question asked [here](https://cmake.org/pipermail/cmake/2018-January/066812.html). Intended to use target_* cmake commands for describing a modular build structure.

##### Project Structure:

``` 
.
├── CMakeLists.txt
├── main.cpp
├── ModA
│   ├── a.cc
│   ├── CMakeLists.txt
│   └── public_includes
│       └── a.h
├── ModB
│   ├── b.cc
│   ├── CMakeLists.txt
│   └── public_includes
│       └── b.h
├── ModC
│   ├── c.cc
│   ├── CMakeLists.txt
│   └── public_includes
│       └── c.h
└── README.md
```
##### Dependency Relations:
```
       +--------+
    +->+main.cpp+<-+
    |  +--------+  |
    |              |
    |              |
    |              |
  +----+        +----+
  |ModA|        |ModB|
  +----+        +----+
    ^              ^
    |              |
    |    +----+    |
    +----+ModC+----+
         +----+

ModA <- ModC: Module A
 depends on Module C
```

##### CMake Scripts:
```
------------------------------------
CMakeLists.txt
------------------------------------
cmake_minimum_required(VERSION 3.0)
project(test_project)

add_subdirectory(ModA)
add_subdirectory(ModB)
add_subdirectory(ModC)

add_executable(main main.cpp)
target_link_libraries(main 
	PRIVATE 
	  ModA ModB)
```

```
------------------------------------
ModA/CMakeLists.txt
------------------------------------
add_library(ModA  a.cc)
target_include_directories(ModA 
	PUBLIC
	  public_includes)
target_link_libraries(ModA PRIVATE ModC)
```

```
------------------------------------
ModB/CMakeLists.txt
------------------------------------
add_library(ModB b.cc)
target_include_directories(ModB 
	PUBLIC 
	  public_includes)
target_link_libraries(ModB PRIVATE ModC)
```

```
------------------------------------
ModC/CMakeLists.txt
------------------------------------
add_library(ModC c.cc)
target_include_directories(ModC 
	PUBLIC 
	  public_includes)
```
