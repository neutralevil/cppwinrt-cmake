cmake_minimum_required(VERSION 3.12.0)

set(CMAKE_SYSTEM_NAME WindowsStore)
set(CMAKE_SYSTEM_VERSION 10.0)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(winrt-cmake)

if(MSVC)
    add_definitions(-D_UNICODE)
endif()

add_executable(winrt-cmake WIN32 main.cpp pch.h pch.cpp)
set_target_properties(winrt-cmake PROPERTIES VS_WINDOWS_TARGET_PLATFORM_MIN_VERSION 10.0.17134.0)
target_link_libraries(winrt-cmake WindowsApp)
target_compile_options(winrt-cmake PRIVATE "/Yupch.h")
target_compile_options(winrt-cmake PRIVATE "/Fp${CMAKE_CFG_INTDIR}/pch.pch")
# get_source_file_property(_compile_flags pch.cpp COMPILE_FLAGS)
# message(FATAL_ERROR ${_compile_flags})
set_source_files_properties(pch.cpp PROPERTIES COMPILE_FLAGS "/Ycpch.h")