cmake_minimum_required(VERSION 3.6)
project(opengl_template)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES main.cpp)
add_executable(opengl_template ${SOURCE_FILES})

find_package(PkgConfig REQUIRED)

pkg_search_module(GLFW REQUIRED glfw3)
include_directories(${GLFW_INCLUDE_DIRS})

pkg_search_module(GLEW REQUIRED glew)
include_directories(${GLEW_INCLUDE_DIRS})

find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

target_link_libraries(opengl_template ${GLFW_STATIC_LIBRARIES})
target_link_libraries(opengl_template ${GLEW_LIBRARIES})
target_link_libraries(opengl_template ${OPENGL_LIBRARIES})



