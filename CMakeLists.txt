cmake_minimum_required(VERSION 3.13)
set(PICO_SDK_PATH ../external/pico-sdk/)
include(pico_sdk_import.cmake)
project(quokka C CXX ASM)
set(CMAKE_C_STANDARD 11)

# Default C Compile Flags
set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fanalyzer" CACHE STRING "Set C Compiler Flags" FORCE)

pico_sdk_init()

# Adds subdirectories
add_subdirectory(kernel)

