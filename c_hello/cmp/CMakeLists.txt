cmake_minimum_required(VERSION 3.23)
project(cmp)

set(CMAKE_CXX_STANDARD 14)

set(CMAKE_OSX_ARCHITECTURES "arm64")
set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O2")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")

find_package(PkgConfig REQUIRED)
pkg_search_module(PROTOBUF REQUIRED protobuf)  # depend on pkg-config, this looks for opencv.pc file

#set(OPENSSL_USE_STATIC_LIBS TRUE)
find_package(OpenSSL REQUIRED)
find_package(SafeheronCryptoSuites REQUIRED)
find_package(CryptoTSSRSA REQUIRED)

add_executable(cmp
        minimal_key_gen_test.cpp  ../CTimer.cpp)

target_include_directories(${PROJECT_NAME} PUBLIC
        ${SafeheronCryptoSuites_INCLUDE_DIRS}
        ${CryptoTSSRSA_INCLUDE_DIRS}
        /usr/local/include  # This directory is included default on linux but not on Mac os
        )

# This directory is included default on linux but not on Mac os
target_link_directories(${PROJECT_NAME} PUBLIC /usr/local/lib)

target_link_libraries(${PROJECT_NAME} PUBLIC
        SafeheronCryptoSuites
        CryptoTSSRSA
        pthread
        OpenSSL::Crypto
        -ldl
        MPCFlow
        gtest
        MultiPartyEcdsa
        )