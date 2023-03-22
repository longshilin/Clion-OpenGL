cmake_minimum_required(VERSION 3.7)
project(Clion-OpenGL) # Your Project Name

if (WIN32)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

    include_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLFW/include)
    link_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLFW/lib-vc2019)

    include_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLEW/include)
    link_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLEW/lib/Release/Win32)
elseif (APPLE)
    set(CMAKE_CXX_FLAGS "-framework Cocoa -framework OpenGL -framework IOKit -framework CoreVideo -std=c++11")

    include_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLFW/include)
    link_directories(${PROJECT_SOURCE_DIR}/Dependencies/GLFW/lib-x86_64)

    include_directories(/usr/local/Cellar/glew/2.2.0_1/include)
    link_directories(/usr/local/Cellar/glew/2.2.0_1/lib)
endif ()

set(SOURCE_FILES OpenGL/src/Application.cpp)
add_definitions(-DGLEW_STATIC)
add_executable(Clion-OpenGL ${SOURCE_FILES})

if (WIN32)
    target_link_libraries(Clion-OpenGL glew32s glfw3 opengl32)
elseif (APPLE)
    target_link_libraries(Clion-OpenGL glew glfw3)
endif ()
