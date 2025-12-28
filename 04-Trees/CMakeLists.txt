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

# target trees library
# ----------------------------------------------------------------------------------------
set(LIBRARY_NAME trees-library)
add_library(${LIBRARY_NAME} STATIC
 "${CMAKE_SOURCE_DIR}/src/dsexceptions.h"
 "${CMAKE_SOURCE_DIR}/src/BinarySearchTree.h"
)
target_link_libraries(${LIBRARY_NAME})
target_include_directories(${LIBRARY_NAME} PUBLIC "${CMAKE_SOURCE_DIR}/src")
set_target_properties(${LIBRARY_NAME} PROPERTIES LINKER_LANGUAGE CXX)

# target binary-search-tree
# ----------------------------------------------------------------------------------------
set(EXECUTABLE_NAME binary-search-tree)
add_executable(${EXECUTABLE_NAME}
  "${CMAKE_SOURCE_DIR}/src/BinarySearchTree.cc"
)
target_link_libraries(${EXECUTABLE_NAME} PUBLIC ${LIBRARY_NAME})
set_target_properties(${EXECUTABLE_NAME} PROPERTIES
RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${PROJECT_NAME})
set_property(TARGET ${EXECUTABLE_NAME} PROPERTY VS_DEBUGGER_WORKING_DIRECTORY $<TARGET_FILE_DIR:${PROJECT_NAME}>)

