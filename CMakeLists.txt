cmake_minimum_required(VERSION 2.8)

project(proxy)
set(CMAKE_CXX_FLAGS
  "$ENV{CXXFLAGS} -rdynamic -O2 -g  -std=c++1z -Wall -Werror -Wno-unused-function -fstack-protector-all")
find_package(zhuyh)
link_directories(/home/zhuyh/Code/GraduationDesign/zhuyh/lib)
set(LIBS 
    zhuyh
    dl
    jsoncpp
    pthread
    yaml-cpp
    mysqlclient
    ssl
    crypto)

include_directories(../zhuyh/src/)

set(LIBS_SRC
    src/LogInServlet.cpp
    src/ProxyUser.cpp
    src/HttpProxyServer.cpp
    src/SecureHttpProxyServer.cpp
    src/main.cpp)

add_executable(Proxy ${LIBS_SRC})
target_link_libraries(Proxy ${LIBS})

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
