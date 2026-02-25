cmake_minimum_required(VERSION 3.20)
project(fem2d LANGUAGES CXX)
option(BUILD_TESTS "Build tests" ON)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_library(femcore src/core/dummy.cpp)

target_include_directories(femcore PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)

add_executable(fem_cli
    apps/fem_cli/main.cpp
)

target_link_libraries(fem_cli PRIVATE femcore)

if(BUILD_TESTS)
    enable_testing()
    add_subdirectory(tests)
endif()