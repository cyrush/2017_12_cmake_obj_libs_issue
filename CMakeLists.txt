cmake_minimum_required(VERSION 3.8)

set(BUILD_SHARED_LIBS OFF)
include(blt/SetupBLT.cmake)

project(example)

add_library(c_stuff
            OBJECT
            c_stuff.c
            c_stuff.h )
            
add_library(cpp_stuff
            OBJECT
            cpp_stuff.cpp
            cpp_stuff.hpp )


add_library(example STATIC 
            example.cpp 
            example.hpp
            $<TARGET_OBJECTS:c_stuff>
            $<TARGET_OBJECTS:cpp_stuff>)

add_executable(driver driver.cpp)

target_link_libraries(driver example)




