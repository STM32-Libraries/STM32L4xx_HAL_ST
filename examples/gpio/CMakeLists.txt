# Minimum required version of CMake
cmake_minimum_required(VERSION 3.22)

# Project name
project(gpio_example)

set(CMAKE_SYSTEM_NAME Linux)

set(CMAKE_SYSTEM_PROCESSOR arm)

# Without this flag, CMake is unable to pass the test compilation check
set(CMAKE_TRY_COMPILE_TARGET_TYPE STATIC_LIBRARY)

# Set msp-gcc for c files
set(CMAKE_C_COMPILER $ENV{HOME}/Tools/gcc-arm/gcc-arm-none-eabi-10.3-2021.10/bin/arm-none-eabi-gcc)

set(PROJECT_VERSION_MAJOR 1)
set(PROJECT_VERSION_MINOR 0)
set(PROJECT_VERSION_PATCH 0)
set(PROJECT_VERSION "${PROJECT_VERSION_MAJOR}_${PROJECT_VERSION_MINOR}_${PROJECT_VERSION_PATCH}")

set(SOURCES
    ${PROJECT_NAME}.c
    ../../startup/startup.c
    system_stm32l4xx.c
    stm32l4xx_it.c
)

# Include directories
include_directories(
                    ../../lib/st/board 
                    ../../lib/st/device 
                    ../../lib/st/core 
                    ../../lib/st/cmsis 
                    .
)

# Compiler flags
set(CMAKE_C_FLAGS "-mcpu=cortex-m4 -nostartfiles -O2 -g -Wall -std=c11 -Wl,-Map=output.map")

# Linker flags
set(CMAKE_EXE_LINKER_FLAGS "-T ../../../linker/linker.ld")

add_subdirectory(../../lib/st st_lib)

# add_executable(Libraries src/library.c)
add_executable(${PROJECT_NAME}${PROJECT_VERSION}.out ${SOURCES} ${PROJECT_NAME}.c)
target_link_libraries(${PROJECT_NAME}${PROJECT_VERSION}.out 
                        st_lib
                        )
