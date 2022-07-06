cmake_minimum_required(VERSION 2.8.12)
project(slam_demo)

set(CMAKE_BUILD_TYPE "Debug")

find_package(Pangolin 0.5 REQUIRED)

find_package(OpenCV REQUIRED)
include_directories(
        ${Pangolin_INCLUDE_DIRS}
        ${OpenCV_INCLUDE_DIRS}
)

add_library(${PROJECT_NAME} SHARED
        src/viz/slam_visualizer.cpp)

target_link_libraries(${PROJECT_NAME}
        ${Pangolin_LIBRARIES}
        ${OpenCV_LIBS})

add_executable(slam_visualization src/viz/test_viz.cpp)
target_link_libraries(slam_visualization ${PROJECT_NAME})