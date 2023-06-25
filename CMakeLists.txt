cmake_minimum_required(VERSION 3.12)

set(FAIRYGUI_LIB_NAME fairygui CACHE PATH "fairygui include directory")
project(fairygui)

OPTION(BUILD_FAIRYGUI_EXAMPLES "Build the fairygui examples" OFF)

# file list
file(GLOB_RECURSE FAIRYGUI_SRC
        ${CMAKE_CURRENT_SOURCE_DIR}/libfairygui/Classes/*.c
        ${CMAKE_CURRENT_SOURCE_DIR}/libfairygui/Classes/*.cc
        ${CMAKE_CURRENT_SOURCE_DIR}/libfairygui/Classes/*.cpp
    )
file(GLOB_RECURSE FAIRYGUI_HEADER
        ${CMAKE_CURRENT_SOURCE_DIR}/libfairygui/Classes/*.h
        ${CMAKE_CURRENT_SOURCE_DIR}/libfairygui/Classes/*.hpp
    )

add_library(${FAIRYGUI_LIB_NAME} ${FAIRYGUI_SRC} ${FAIRYGUI_HEADER})

target_link_libraries(${FAIRYGUI_LIB_NAME} PRIVATE cocos2d)
set(FAIRYGUI_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libfairygui/Classes CACHE PATH "fairygui include directory")
target_include_directories(${FAIRYGUI_LIB_NAME} PUBLIC ${FAIRYGUI_INCLUDE_DIR})

target_compile_features(${FAIRYGUI_LIB_NAME} PRIVATE cxx_std_17)
target_compile_options(${FAIRYGUI_LIB_NAME} PRIVATE -Wall)
