cmake_minimum_required(VERSION 3.5.0)
project(trees VERSION 1.0.0)

include(FetchContent)

# build type and others
# ----------------------------------------------------------------------------------------
set(CMAKE_BUILD_TYPE Debug)

# generate compile_commands.json
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# c standard
# ----------------------------------------------------------------------------------------
set(CMAKE_CXX_STANDARD          17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS        OFF)

# compile options
# ----------------------------------------------------------------------------------------
if(CMAKE_CXX_COMPILER_ID MATCHES "GNU") 
  add_compile_options(
    -Wall
    -Wno-enum-compare
    -Wno-error=maybe-uninitialized
  )
elseif(CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
  add_compile_options(/W4)
endif()

# target binary-search-tree
# ----------------------------------------------------------------------------------------
set(BINARY_SEARCH_TREE_EXECUTABLE binary-search-tree)
add_executable(${BINARY_SEARCH_TREE_EXECUTABLE}
  "${CMAKE_SOURCE_DIR}/src/01-TestBinarySearchTree.cc"
  "${CMAKE_SOURCE_DIR}/src/01-BinarySearchTree.h"
  "${CMAKE_SOURCE_DIR}/src/dsexceptions.h"
)

# target avl-tree
# ----------------------------------------------------------------------------------------
set(AVL_TREE_EXECUTABLE avl-tree)
add_executable(${AVL_TREE_EXECUTABLE}
  "${CMAKE_SOURCE_DIR}/src/02-TestAvlTree.cc"
  "${CMAKE_SOURCE_DIR}/src/02-AvlTree.h"
  "${CMAKE_SOURCE_DIR}/src/dsexceptions.h"
)

# target splay-tree
# ----------------------------------------------------------------------------------------
set(SPLAY_TREE_EXECUTABLE splay-tree)
add_executable(${SPLAY_TREE_EXECUTABLE}
  "${CMAKE_SOURCE_DIR}/src/03-TestSplayTree.cc"
  "${CMAKE_SOURCE_DIR}/src/03-SplayTree.h"
  "${CMAKE_SOURCE_DIR}/src/dsexceptions.h"
)
