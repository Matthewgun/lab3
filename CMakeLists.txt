cmake_minimum_required(VERSION 3.5.0)  # Set the minimum required version of CMake

# Set the patch version as an internal cache variable
set(PATCH_VERSION "1" CACHE INTERNAL "Patch version")

# Define the project version using the patch version
set(PROJECT_VERSION 0.0.${PATCH_VERSION})

# Define the project name and version
project(coollab2 VERSION ${PROJECT_VERSION})

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set the package name for CPack
set(CPACK_PROJECT_NAME coollab2)

# Configure CPack for package generation
if (CMAKE_SYSTEM_NAME STREQUAL "Linux")
    set(CPACK_GENERATOR DEB)  # Set generator for DEB packages on Linux
    set(CPACK_DEBIAN_PACKAGE_DEPENDS "libgtk-3-dev;libstdc++6-dev")  # Specify package dependencies
elseif (CMAKE_SYSTEM_NAME STREQUAL "Darwin")
    set(CPACK_GENERATOR ZIP)  # Set generator for ZIP packages on macOS
endif()

# Set package version information for CPack
set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")

# Set contact information for the package maintainer
set(CPACK_PACKAGE_CONTACT example@example.com)

# Include CPack to enable packaging functionality
include(CPack)

# Enable testing functionality in CMake
enable_testing()

# Add executable target with valid name and source files
add_executable(coollab2 main.cpp )  # Ensure all source files are included
