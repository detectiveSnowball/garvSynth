cmake_minimum_required(VERSION 3.22)

project(garvSynth)

set(CMAKE_CXX_STANDARD 23)

set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libs) 

#We are going to download cpm, a cmake package manager.
include(cmake/get_cpm.cmake)


CPMAddPackage(
    NAME JUCE
    GITHUB_REPOSITORY juce-framework/JUCE
    GIT_TAG 7.0.8
    VERSION 7.0.8
    SOURCE_DIR ${LIB_DIR}/juce
)


if (MSVC)
    add_compile_options(/Wall /WX)
else()
    add_compile_options(-Wall -Wextra -Wpedantic)
endif()

add_subdirectory(plugin)
