cmake_minimum_required(VERSION 3.19)

set(EXECUTABLE_NAME pet_terraria)

project(${EXECUTABLE_NAME})


if (MSVC)
  set(CMAKE_CXX_FLAGS "/std:c++latest ${CMAKE_CXX_FLAGS}")
else()
  set(CMAKE_CXX_STANDARD 20)
  set(CMAKE_CXX_STANDARD_REQUIRED True)
  set(CMAKE_CXX_FLAGS_RELEASE -O3)
endif()

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(SFML 2.5 COMPONENTS system window graphics audio REQUIRED)
find_package(Threads)

set(INCLUDE_DIR include)
set(SRC_DIR src)

file(GLOB SRCS
  ${SRC_DIR}/*.cpp
  )

include_directories(
  ${INCLUDE_DIR}
  )

add_executable(${EXECUTABLE_NAME} ${SRCS})

target_link_libraries(${EXECUTABLE_NAME} ${CMAKE_THREAD_LIBS_INIT} sfml-graphics sfml-audio)
