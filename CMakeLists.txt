cmake_minimum_required(VERSION 3.16)

set(CMAKE_CXX_STANDARD_LIBRARY "GNU")
project(cudaDemos LANGUAGES CXX CUDA)
set(CMAKE_CXX_STANDARD_LIBRARY "GNU")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_VERBOSE_MAKEFILE ON)

#set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static-libstdc++")

add_executable(cudaDemos main.cpp
       )

include(GNUInstallDirs)
install(TARGETS cudaDemos
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

set(CUDA_LIB_PATH "/opt/cuda/lib64")
file(GLOB CUDA_LIBS "${CUDA_LIB_PATH}/*.so")


#add_library(cudalibx hello.cu hello.h)
#target_compile_features(cudalibx PUBLIC cxx_std_17)

find_package(g3log CONFIG REQUIRED)

add_subdirectory(cudalibxSrc)

target_link_libraries(cudaDemos PRIVATE g3log ${CUDA_LIBS} cudalibx)


