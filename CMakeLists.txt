cmake_minimum_required(VERSION 4.3)

project(stashii-thread-pool LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(threadpool INTERFACE)
target_include_directories(threadpool INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include)

find_package(Threads REQUIRED)
target_link_libraries(threadpool INTERFACE Threads::Threads)

add_executable(example main.cpp)
target_link_libraries(example PRIVATE threadpool)