
cmake_minimum_required(VERSION 3.0)
PROJECT(EMPLOYEE_SYSTEM)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")

set(CMAKE_BUILD_TYPE Debug)

include_directories(${CMAKE_CURRENT_LIST_DIR}/inc)

#pinocchio setting
set(PINOCCHIO_DIR /home/cosmic/code/pinocchio/build)
include_directories(${PINOCCHIO_DIR}/include)
# link_directories(${PINOCCHIO_DIR}/src)


#Eigen3 setting
find_package (Eigen3 REQUIRED)
# checking property of the target
get_target_property(inc_dir Eigen3::Eigen INTERFACE_INCLUDE_DIRECTORIES)
include_directories(${inc_dir})

set(SRC 
    src/test.cpp)

add_executable(mytest ${SRC})
target_link_libraries(mytest ${PINOCCHIO_DIR}/src/libpinocchio.so)
