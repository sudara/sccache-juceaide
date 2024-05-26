cmake_minimum_required(VERSION 3.25)
project(sccache-juce VERSION 1.0.0)

find_program(SCCACHE sccache)

if (SCCACHE)
    set(CMAKE_C_COMPILER_LAUNCHER ${SCCACHE} CACHE INTERNAL "")
    set(CMAKE_CXX_COMPILER_LAUNCHER ${SCCACHE} CACHE INTERNAL "")
endif()

add_subdirectory(JUCE)
juce_add_console_app(sccache-juce)
target_sources(sccache-juce PRIVATE main.cpp)
target_compile_definitions(sccache-juce PUBLIC JUCE_USE_CURL=0 JUCE_WEB_BROWSER=0)
