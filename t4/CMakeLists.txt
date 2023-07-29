cmake_minimum_required(VERSION 3.23)

project(usehello)
add_subdirectory(src)

# set(CMAKE_INSTALL_PREFIX "install_path")
#[[
特殊的环境变量 CMAKE_INCLUDE_PATH 和 CMAKE_LIBRARY_PATH
这两个是环境变量而不是 cmake 变量
使用方法是要在 bash 中用 export
]]