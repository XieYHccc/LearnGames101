cmake_minimum_required(VERSION 3.10)
project(RayTracing)

set(CMAKE_CXX_STANDARD 17)

add_executable(RayTracing main.cpp Object.hpp Renderer.hpp Vector.hpp Sphere.hpp global.hpp Triangle.hpp Scene.cpp Scene.hpp Light.hpp Renderer.cpp)

if (CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
    target_compile_options(RayTracing PUBLIC -Wall -Wextra -pedantic -Wshadow -Wreturn-type -fsanitize=undefined)
    target_link_libraries(RayTracing PUBLIC -fsanitize=undefined)
elseif (CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
    target_compile_options(RayTracing PUBLIC /W4 /permissive-)
endif()

target_compile_features(RayTracing PUBLIC cxx_std_17)