cmake_minimum_required(VERSION 3.17)
project(my_WebServer)
set(CMAKE_CXX_STANDARD 14)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# 添加寻找FindSFML.cmake文件的路径
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmakeModule/;${CMAKE_MODULE_PATH};")
# 查找第三方库
find_package(MySQL REQUIRED)

# 添加执行程序
SET(CODE_SRC main.cpp ./timer/lst_timer.cpp ./http/http_conn.cpp ./log/log.cpp ./CGImysql/sql_connection_pool.cpp  webserver.cpp config.cpp)
add_executable(my_WebServer ${CODE_SRC})

# 添加pthread,mysql支持
target_link_libraries(my_WebServer  ${MYSQL_LIB})
include_directories(${MYSQL_INCLUDE_DIR})