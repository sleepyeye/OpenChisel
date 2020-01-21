cmake_minimum_required(VERSION 3.13)

project(OpenChisel LANGUAGES CXX)

# Setup projects
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/cmake/")
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CXX_STANDARD_REQUIRED YES)
set(CMAKE_CXX_STANDARD 17)

# Add external dependancies
add_subdirectory(extern)

# Add OpenChisel library
add_library(OpenChisel SHARED)
target_link_libraries(OpenChisel PUBLIC Eigen3::Eigen)
target_include_directories(OpenChisel PUBLIC include)
add_subdirectory(include)
add_subdirectory(src)


