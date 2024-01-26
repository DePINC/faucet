cmake_minimum_required(VERSION 3.10)

set(CMAKE_TOOLCHAIN_FILE ${CMAKE_CURRENT_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake)

project(depinc-faucet)

find_package(plog CONFIG REQUIRED)
find_package(cxxopts CONFIG REQUIRED)
find_package(CURL CONFIG REQUIRED)
find_package(jsoncpp CONFIG REQUIRED)
find_package(asio CONFIG REQUIRED)

set(BF_SRCS
    src/main.cpp
    src/http_client.cpp
    src/rpc_client.cpp
)

add_executable(depinc-faucet ${BF_SRCS})
target_link_libraries(depinc-faucet PRIVATE plog::plog cxxopts::cxxopts CURL::libcurl JsonCpp::JsonCpp asio asio::asio)
target_compile_features(depinc-faucet PRIVATE cxx_std_17)
