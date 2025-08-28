cmake_minimum_required(VERSION 3.30)
# set(CMAKE_EXPERIMENTAL_CXX_IMPORT_STD 0e5b6991-d74f-4b3d-a41c-cf096e0b2508)
set(PROJECT_NAME run)
set(EXECUTABLE run)
project(${PROJECT_NAME} LANGUAGES CXX)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
# set(CMAKE_CXX_MODULE_STD ON)

# 先创建空的可执行目标
add_executable(${EXECUTABLE})

# 自动收集 src 目录下所有源文件（含子目录）
file(GLOB_RECURSE SRC_FILES
     CONFIGURE_DEPENDS
     ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp)

target_sources(${EXECUTABLE}
    PRIVATE
        ${SRC_FILES}
)

target_include_directories(${EXECUTABLE}
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)
