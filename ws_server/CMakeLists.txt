cmake_minimum_required(VERSION 3.3)

project(ws_server LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(libhv REQUIRED)

function(add_libhv_executable name source)
  add_executable(${name} ${source})
  target_link_libraries(${name} PUBLIC hv)
  target_include_directories(${name} PUBLIC ${hv_INCLUDE_DIRS})
endfunction()

add_libhv_executable(relay_server src/relay_server.cpp)

add_libhv_executable(client1 src/client1.cpp)

add_libhv_executable(client2 src/client2.cpp)
