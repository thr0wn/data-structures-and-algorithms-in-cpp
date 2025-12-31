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
    -Wno-sign-compare
  )
elseif(CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
  add_compile_options(/W4)
endif()

# target test-max-sum
# ----------------------------------------------------------------------------------------
set(BINARY_SEARCH_TREE_EXECUTABLE test-max-sum)
add_executable(${BINARY_SEARCH_TREE_EXECUTABLE}
  "${CMAKE_SOURCE_DIR}/src/01-TestMaxSum.cc"
)

# target test-binary-search
# ----------------------------------------------------------------------------------------
set(AVL_TREE_EXECUTABLE test-binary-search)
add_executable(${AVL_TREE_EXECUTABLE}
  "${CMAKE_SOURCE_DIR}/src/02-TestBinarySearch.cc"
)

# target test-euclid
# ----------------------------------------------------------------------------------------
set(SPLAY_TREE_EXECUTABLE test-euclid)
add_executable(${SPLAY_TREE_EXECUTABLE}
  "${CMAKE_SOURCE_DIR}/src/03-TestEuclid.cc"
)

# target test-exponentiation
# ----------------------------------------------------------------------------------------
set(SPLAY_TREE_EXECUTABLE test-exponentiation)
add_executable(${SPLAY_TREE_EXECUTABLE}
  "${CMAKE_SOURCE_DIR}/src/04-TestExponentiation.cc"
)
