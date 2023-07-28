cmake_minimum_required(VERSION 3.23)
PROJECT(HELLO)

# set(CMAKE_INSTALL_PREFIX /usr)
# ADD_SUBDIRECTORY(source_dir [binary_dir] [EXCLUDE_FROM_ALL])这个指令用于向当前工程添加存放源文件的子目录，
# 并可以指定中间二进制和目标二进制存放的位置。
set(CMAKE_INSTALL_PREFIX share) # make install安装位置的前缀
message(STATUS ${CMAKE_INSTALL_PREFIX})
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)
install(PROGRAMS runhello.sh DESTINATION bin)
install(FILES COPYRIGHT README DESTINATION share/doc/cmake/t2)

# 注意如果不想要连带目录一起安装，那就多加一个斜杠
install(DIRECTORY doc/ DESTINATION share/doc/cmake/t2)

# bin是指明安装到哪
ADD_SUBDIRECTORY(src bin)
