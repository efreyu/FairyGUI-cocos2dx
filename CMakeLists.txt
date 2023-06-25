cmake_minimum_required(VERSION 3.12)

project(fairygui)

OPTION(BUILD_FAIRYGUI_EXAMPLES "Build the fairygui examples" OFF)

# file list
file(GLOB_RECURSE FAIRYGUI_SRC Classes/*.c Classes/*.cc Classes/*.cpp)
file(GLOB_RECURSE FAIRYGUI_HEADER Classes/*.h Classes/*.hpp)

add_library(fairygui ${FAIRYGUI_SRC} ${FAIRYGUI_HEADER})

target_link_libraries(fairygui PRIVATE cocos2d)
target_include_directories(fairygui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/Classes)
