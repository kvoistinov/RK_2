cmake_minimum_required(VERSION 3.10)

project(rk_2)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_COMPILER g++) 

include_directories(./source/)

add_executable(rk_2 pattern_memento.cpp)
