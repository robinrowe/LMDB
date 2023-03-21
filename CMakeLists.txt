# libunistd/lmdb/CMakeLists.txt

# git clone git://git.openldap.org/openldap.git --branch OPENPROJECT_NAME_REL_ENG_2_4

cmake_minimum_required(VERSION 3.8)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

project(liblmdb)
message("--- Building library ${PROJECT_NAME} ---")

message("CMAKE_CURRENT_SOURCE_DIR = ${CMAKE_CURRENT_SOURCE_DIR}")
message("BINARY_DIR = ${CMAKE_BINARY_DIR}/${CMAKE_GENERATOR_PLATFORM}")

if(WIN32)
#	include_directories("${CMAKE_CURRENT_SOURCE_DIR}/../../unistd")
	link_directories(${CMAKE_BINARY_DIR}/${CMAKE_GENERATOR_PLATFORM})
#	link_libraries(libunistd)
endif(WIN32)

file(STRINGS CMakeSources.txt SOURCES)

if(WIN32)
	message("Suppressing Windows warnings for lmdb")
	add_definitions(-D_CRT_SECURE_NO_WARNINGS)
	add_definitions(-D_CRT_SECURE_NO_DEPRECATE)
	add_definitions(-D_CRT_NONSTDC_NO_DEPRECATE)
	include_directories(getopt)
endif(WIN32)

#necessary for building mdb_dkey for mtest6:
add_definitions(-DMDB_DEBUG)

set(INCDIR ${CMAKE_CURRENT_SOURCE_DIR}/liblmdb)
if(WIN32)
set(WIN_SOURCES getopt/getopt.c)
endif(WIN32)

add_library(${PROJECT_NAME} STATIC ${SOURCES} ${WIN_SOURCES})
target_include_directories(${PROJECT_NAME} PUBLIC ${INCDIR})
add_subdirectory(test)
