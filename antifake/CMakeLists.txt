cmake_minimum_required(VERSION 3.18.1)
project(AntiFakerAndroidChecker)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(
        emulator_check
        SHARED
        src/main/jni/emulator/emcheck64.c
)

add_library(
        property_get
        SHARED
        src/main/jni/property/proget.c
)

find_library(log-lib log)

target_link_libraries(emulator_check ${log-lib})
target_link_libraries(property_get ${log-lib})
