cmake_minimum_required(VERSION 3.7)
project(Clion-OpenGL) # Your Project Name

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(SOURCE_FILES OpenGL/src/Application.cpp)

include_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLFW/include)
link_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLFW/lib-vc2019)

include_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLEW/include)
link_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLEW/lib/Release/Win32)

add_definitions(-DGLEW_STATIC)

add_executable(Clion-OpenGL ${SOURCE_FILES})
target_link_libraries(Clion-OpenGL glew32s glfw3 opengl32 User32 Gdi32 Shell32)
