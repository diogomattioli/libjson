cmake_minimum_required(VERSION 3.16)
project(lib_template CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "-Wall -Wextra -Wpedantic -Werror")
set(CMAKE_CXX_FLAGS_DEBUG "-g3")
set(CMAKE_CXX_FLAGS_RELEASE "-O3")

find_package(GTest REQUIRED)

include_directories("include")
link_directories(${CMAKE_CURRENT_BINARY_DIR})

file(GLOB srcs "src/*.cpp")
add_library(${CMAKE_PROJECT_NAME} ${srcs})

file(GLOB tests "tests/*.cpp")
add_executable(${CMAKE_PROJECT_NAME}-tests ${srcs} ${tests})
target_link_libraries(${CMAKE_PROJECT_NAME}-tests ${CMAKE_PROJECT_NAME} ${GTEST_BOTH_LIBRARIES})
