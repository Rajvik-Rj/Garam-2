cmake_minimum_required(VERSION 3.15)

project(GARAM)

set(CMAKE_CXX_STANDARD 17)

include(FetchContent)

FetchContent_Declare(
  clap
  GIT_REPOSITORY https://github.com/free-audio/clap.git
  GIT_TAG main
)

FetchContent_MakeAvailable(clap)

add_library(GARAM MODULE src/garam.cpp)

target_include_directories(GARAM PRIVATE
  ${clap_SOURCE_DIR}/include
)

set_target_properties(GARAM PROPERTIES
  PREFIX ""
  SUFFIX ".clap"
)
