cmake_minimum_required(VERSION 3.23)
include_directories(/usr/include/hello)

#[[
特殊的环境变量 CMAKE_INCLUDE_PATH 和 CMAKE_LIBRARY_PATH
这两个是环境变量而不是 cmake 变量
使用方法是要在 bash 中用 export

通过bash export：export CMAKE_INCLUDE_PATH=/usr/include/hello。可以用下面来搜索头文件

find_path(myheader hello.h)
if(myheader)
    include_directories(${myheader})
endif(myheader)
同理，CMAKE_LIBRARY_PATH可以结合find_library使用
]]
add_executable(main main.cpp)

# 添加需要链接的共享库
target_link_libraries(main libhello.so)