set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CXX_STANDARD_LIBRARY "GNU")
enable_language(CUDA)

set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static-libstdc++")

set(BUILD_SHARED_LIBS ON)

add_library(cudalibx SHARED
hello.cu
hello.h



)
target_compile_features(cudalibx PUBLIC cxx_std_17)
set_target_properties(cudalibx
                       PROPERTIES CUDA_SEPARABLE_COMPILATION ON)
target_link_libraries(cudalibx)


