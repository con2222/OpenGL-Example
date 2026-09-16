# This defines the minimum required CMake version to build this project.
cmake_minimum_required(VERSION 3.14...4.2)

# This is your project (or module, for modular projects) name.
project(OpenGL_Example)

# Instructs the compiler that we are using the C++ 23 standard.
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)


find_package(OpenGL REQUIRED)

# Same as above but for GLFW
find_package(glfw3 3.3 REQUIRED)

# Same as above but for glm.
find_package(glm REQUIRED)

# This command adds a build target (executable or library, use add_library for libraries).
# The first word is the name of the executable and everything after that is the source files you want to include in
# this new target.
add_executable(OpenGL_Example main.cpp vendor/glad/gl.c)
target_include_directories(OpenGL_Example PRIVATE vendor/glad/include)

# This links libraries against a target, the target being the executable we just added.
target_link_libraries(OpenGL_Example PRIVATE OpenGL::GL  glfw glm::glm ${CMAKE_DL_LIBS} )

