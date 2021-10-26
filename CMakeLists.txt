cmake_minimum_required(VERSION 2.8)
project(fibercpp CXX)

# set(Boost_USE_STATIC_LIBS TRUE)

find_package(Threads REQUIRED)
find_package(Boost 1.62 REQUIRED context fiber COMPONENTS)

file(GLOB WorkSharing work_sharing.cpp)
file(GLOB Barrier barrier.cpp)

# add_executable(${PROJECT_NAME} ${Barrier})
add_executable(${PROJECT_NAME} ${WorkSharing})

target_link_libraries(${PROJECT_NAME} PRIVATE
    pthread
    ${Boost_CONTEXT_LIBRARY}
    ${Boost_FIBER_LIBRARY})
