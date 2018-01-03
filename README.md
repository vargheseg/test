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
