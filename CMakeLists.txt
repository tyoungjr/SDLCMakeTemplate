cmake_minimum_required(VERSION 3.22)

project(SDLTutorial VERSION 1.0.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

option(USE_CPM "Whether to use CPM" ON)

set(LIBRARY_NAME lib)
set(EXECUTABLE_NAME sdl2testmebaby)

set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake/")

option(ENABLE_WARNINGS "Enable compiler warnings for a target" ON)
option(ENABLE_WARNINGS_AS_ERRORS "Enable compiler warnings as errors" OFF)


if(ENABLE_WARNINGS)
    include(Warnings)
endif()

include(AddGitSubmodule)
include(FetchContent)


# Define SDL2 installation directory
set(SDL2_INSTALL_DIR "${CMAKE_BINARY_DIR}/external/SDL2-install")

include(ExternalProject)
# Add an external project for SDL2
ExternalProject_Add(
    SDL2
    GIT_REPOSITORY https://github.com/libsdl-org/SDL.git
    GIT_TAG release-2.28.3 # Use a stable release
    PREFIX "${CMAKE_BINARY_DIR}/external/SDL2"
    CMAKE_ARGS
        -DCMAKE_BUILD_TYPE=Release
        -DCMAKE_INSTALL_PREFIX=${SDL2_INSTALL_DIR}
    BUILD_ALWAYS OFF# Ensures the build runs each time or not
    )

# Add the SDL2 installation directory to the CMake search path
list(APPEND CMAKE_PREFIX_PATH "${SDL2_INSTALL_DIR}")

add_subdirectory(external)
add_subdirectory(app)
