cmake_minimum_required(VERSION 3.16 FATAL_ERROR)

include(CMake/Vcpkg.cmake)

project(
    "HelloVcpkg"
    VERSION 0.1.0
    LANGUAGES CXX
)

add_definitions(-DUNICODE)
add_definitions("/MP")

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(USE_FOLDERS ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(SRC_HEADERFILES )
set(SRC_SOURCEFILES )
set(SRC_MAIN Source/Main.cpp)

set(PRJ_LIBRARIES
    glad::glad
    glfw
)

find_package(glad CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)

add_executable(${PROJECT_NAME} ${SRC_HEADERFILES} ${SRC_SOURCEFILES} ${SRC_MAIN})
target_link_libraries(${PROJECT_NAME} PRIVATE ${PRJ_LIBRARIES})

set(DIRECTORY PROPERTY VS_STARTUP_PROJECT "HelloVcpkg")
