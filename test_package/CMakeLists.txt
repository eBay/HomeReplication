cmake_minimum_required(VERSION 3.11)
project(test_package)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

find_package(HomeReplication QUIET REQUIRED)

link_directories(${spdk_LIB_DIRS} ${dpdk_LIB_DIRS})

add_executable(${PROJECT_NAME} test_package.cpp)
target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_17)
target_link_libraries(${PROJECT_NAME} HomeReplication::mock
        ${spdk_LIBRARY_LIST}
        ${dpdk_LIBRARY_LIST}
        )
