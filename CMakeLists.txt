cmake_minimum_required(VERSION 3.6)
project(opengl_template)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES main.cpp)
add_executable(learn_opengl ${SOURCE_FILES})

find_package(PkgConfig REQUIRED)

pkg_search_module(GLFW REQUIRED glfw3)
include_directories(${GLFW_INCLUDE_DIRS})

pkg_search_module(GLEW REQUIRED glew)
include_directories(${GLEW_INCLUDE_DIRS})

find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

target_link_libraries(learn_opengl ${GLFW_STATIC_LIBRARIES})
target_link_libraries(learn_opengl ${GLEW_LIBRARIES})
target_link_libraries(learn_opengl ${OPENGL_LIBRARIES})

IF(APPLE)
    find_library(COCOA_LIBRARY Cocoa)
    find_library(IOKIT_LIBRARY IOKit)
    find_library(COREVIDEO_LIBRARY CoreVideo)
    set(EXTRA_LIBS ${COCOA_LIBRARY} ${IOKIT_LIBRARY} ${COREVIDEO_LIBRARY})
    target_link_libraries(learn_opengl ${EXTRA_LIBS})
ENDIF(APPLE)



