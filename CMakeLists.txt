cmake_minimum_required(VERSION 3.8)
project(kassow_kord_vendor)

find_package(ament_cmake REQUIRED)

# force install to current package install
set(CMAKE_INSTALL_PREFIX "${CMAKE_INSTALL_PREFIX}" CACHE STRING "Install prefix" FORCE)

set(KORD_WITH_TESTS OFF CACHE BOOL "Disable tests" FORCE)
set(KORD_WITH_EXAMPLES OFF CACHE BOOL "Disable examples" FORCE)
set(KORD_WITH_DOCS OFF CACHE BOOL "Disable docs" FORCE)
set(KORD_WITH_COVERAGE OFF CACHE BOOL "Disable coverage" FORCE)

set(INSTALL_KORD_API ON CACHE BOOL "Install the API" FORCE)
set(INSTALL_KORD_PROTOCOL ON CACHE BOOL "Install the protocol" FORCE)

include(FetchContent)
FetchContent_Declare(
    kord_api
    GIT_REPOSITORY  https://gitlab.com/kassowrobots/kord-api.git
    GIT_TAG         v3.0.1
    GIT_SHALLOW     true
)

FetchContent_MakeAvailable(kord_api)

ament_package(
  CONFIG_EXTRAS "cmake/kassow_kord_vendor-extras.cmake"
)
