cmake_minimum_required(VERSION 3.22.1)
project(fetch_add_respond)

set(CMAKE_CXX_STANDARD 17)

add_definitions(-DDOCA_ALLOW_EXPERIMENTAL_API)

add_compile_options(-std=c++11 -g -Wall -pthread -I./)

include_directories(/opt/mellanox/doca/include/)
link_directories(/opt/mellanox/doca/lib/x86_64-linux-gnu/)
link_directories(/opt/mellanox/flexio/lib/)

add_executable(fetch_add_respond main.cpp
    rdma_common.cpp
    rdma_common.h
        rdma_fetch_add_respond.cpp
        rdma_fetch_add_respond.h
)

target_link_libraries(fetch_add_respond flexio doca_common stdc++ ibverbs mlx5 pthread doca_rdma doca_argp)

