cmake_minimum_required(VERSION 3.10)
project(imgui)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED True)

file(GLOB ROOT_SOURCE *.cpp)
file(GLOB ROOT_HEADER *.h)

set(BACKENDS
    backends/imgui_impl_sdl3.h
    backends/imgui_impl_sdl3.cpp
    backends/imgui_impl_sdlgpu3.h
    backends/imgui_impl_sdlgpu3.cpp
)

add_subdirectory(../SDL SDL3)

add_library(imgui STATIC ${ROOT_SOURCE} ${ROOT_HEADER} ${BACKENDS})

target_link_libraries(imgui PRIVATE SDL3::SDL3-shared)
target_include_directories(imgui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/backends)
