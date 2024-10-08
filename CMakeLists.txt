cmake_minimum_required(VERSION 3.29)

set(CMAKE_CXX_STANDARD 26)
set(PROJECT_NAME learn-opengl)

project(${PROJECT_NAME})

# Setup libraries
include(FetchContent)
FetchContent_Declare(glfw GIT_REPOSITORY https://github.com/glfw/glfw.git GIT_TAG master)
FetchContent_Declare(glad GIT_REPOSITORY https://github.com/SasLuca/MyGlad.git GIT_TAG master)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

FetchContent_MakeAvailable(glfw)
FetchContent_MakeAvailable(glad)

file(GLOB_RECURSE sources src/*.cpp src/*.c)

add_executable(${PROJECT_NAME} ${sources})
target_link_libraries(${PROJECT_NAME} PRIVATE glad glfw)
set_property(TARGET ${PROJECT_NAME} PROPERTY C_STANDARD 99)