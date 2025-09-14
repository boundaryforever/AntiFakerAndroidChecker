cmake_minimum_required(VERSION 3.18.1)
project(AntiFakerAndroidChecker)

# C 标准与 C++ 标准
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 64 位 so 库
add_library(
        emulator_check
        SHARED
        src/main/jni/emulator/emcheck64.c
)

# property_get so 库
add_library(
        property_get
        SHARED
        src/main/jni/property/proget.c
)

# 查找 NDK log 库
find_library(log-lib log)

# 关联 log 库
target_link_libraries(emulator_check ${log-lib})
target_link_libraries(property_get ${log-lib})
