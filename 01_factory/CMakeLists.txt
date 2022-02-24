# cmake最低版本号要求
cmake_minimum_required(VERSION 3.5)
project(hello)
# add_subdirectory(src bin)
# install_files(readme DESTINATION share/doc/cmake/)
# install_programs(runhello.sh DESTINATION bin)

message(${CMAKE_CURRENT_LIST_DIR})

SET(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_LIST_DIR}/install)
# set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/install)



#################   2   ################

# 设置PROJECT_NAME变量
# set(PROJECT_NAME new_project)

# 设置工程名
# project (${PROJECT_NAME})

SET(CMAKE_CXX_STANDARD 11)
SET(CMAKE_INCLUDE_CURRENT_DIR ON)
SET(CMAKE_AUTOMOC ON)
SET(CMAKE_AUTOUIC ON)
SET(CMAKE_AUTORCC ON)


# 查找当前目录下的所有源文件并存入DIR_SRCS变量
aux_source_directory(src DIR_SRCS)
# 添加一个可编译的目标到工程
add_executable (${PROJECT_NAME} ${DIR_SRCS})


# ###############   1   ###############
# # # 递归列出所有源文件
# # file (GLOB_RECURSE SOURCE_FILES src/*.cpp)
# # # 添加一个可编译的目标到工程
# # add_executable (${PROJECT_NAME} ${SOURCE_FILES})

# # add_executable(${PROJECT_NAME} src/main.cpp)


install(FILES readme DESTINATION doc)
install(PROGRAMS runhello.sh DESTINATION bin)
install(DIRECTORY doc/ DESTINATION doc)
install(TARGETS hello DESTINATION bin)