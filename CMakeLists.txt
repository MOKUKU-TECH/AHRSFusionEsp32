# ESP-IDF component; other builds use upstream's project below.
if(ESP_PLATFORM)
    file(GLOB sources "Fusion/*.c")
    idf_component_register(SRCS ${sources} INCLUDE_DIRS "Fusion")
    return()
endif()

cmake_minimum_required(VERSION 3.15)
project(Fusion)

add_subdirectory("Fusion")
add_subdirectory("Examples/C/Advanced")
add_subdirectory("Examples/C/Simple")
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    add_subdirectory("Python/imufusion") # do not include when run by CI
endif()
