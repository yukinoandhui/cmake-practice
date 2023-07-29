aux_source_directory(. LIBHELLO_SRC)
message(STATUS ${LIBHELLO_SRC})

# 注意要install,且这里设置没用，要在最外面的文件中设置，因为存在变量的作用域问题
set(CMAKE_INSTALL_PREFIX "install_path")
message(STATUS ${CMAKE_INSTALL_PREFIX})

# set(LIBRARY_OUTPUT_PATH bin)
add_library(hello SHARED ${LIBHELLO_SRC})

# 直接add相同名字则不会构建静态库，而改名后又不是我们想要的名字，所以需要联合使用
add_library(hello_static STATIC ${LIBHELLO_SRC})
set_target_properties(hello_static PROPERTIES OUTPUT_NAME "hello")

get_target_property(OUTPUT_VALUE hello_static OUTPUT_NAME)
message(STATUS "This is the hello_static output name: ${OUTPUT_VALUE}")

# # 添加版本号：VERSION 指代动态库版本，SOVERSION 指代 API 版本
# 一般动态链接库都会有版本号
set_target_properties(hello PROPERTIES VERSION 1.2 SOVERSION 1)
install(TARGETS hello hello_static LIBRARY DESTINATION lib ARCHIVE DESTINATION lib)
