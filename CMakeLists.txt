cmake_minimum_required(VERSION 3.15)
project(message-queue LANGUAGES CXX)

find_package(MPI REQUIRED)

add_library(library INTERFACE)
target_include_directories(library INTERFACE include)
target_link_libraries(library INTERFACE MPI::MPI_CXX)
target_compile_options(library INTERFACE -std=c++17)

add_executable(example example.cpp)
target_link_libraries(example library)
