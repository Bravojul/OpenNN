# Specify the minimum version for CMake

cmake_minimum_required(VERSION 2.8.10)

# Project's name

project(pima_indians_diabetes)

if (WIN32)
    if (CMAKE_GENERATOR MATCHES "Visual Studio 15 2017")
		set (PROJECT_LINK_LIBS ${CMAKE_SOURCE_DIR}/build/opennn/Release/opennn.lib)
	else()
		set (PROJECT_LINK_LIBS ${CMAKE_SOURCE_DIR}/build/opennn/libopennn.a)
	endif()
endif (WIN32)

if (UNIX)
    if (CMAKE_GENERATOR MATCHES "Visual Studio 15 2017")
		set (PROJECT_LINK_LIBS ${CMAKE_SOURCE_DIR}/build/opennn/Release/opennn.lib)
	else()
		set (PROJECT_LINK_LIBS ${CMAKE_SOURCE_DIR}/build/opennn/libopennn.a)
	endif()
endif (UNIX)

include_directories(./data)

FILE(COPY ./data/pima_indians_diabetes.dat DESTINATION "${PROJECT_BINARY_DIR}/data")

link_directories(${CMAKE_SOURCE_DIR}/opennn)

include_directories(${CMAKE_SOURCE_DIR}/opennn)

add_executable(pima_indians_diabetes main.cpp)

target_link_libraries(pima_indians_diabetes ${PROJECT_LINK_LIBS})
