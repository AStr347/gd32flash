cmake_minimum_required(VERSION 3.5) # check CMake ver

include(libbuilder.cmake)

project(gd32flash)# set name of project


#set Release/Debug dir place
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "..")

set(SOURCEDIR ${PROJECT_SOURCE_DIR}/src)

add_executable(${PROJECT_NAME} ${SOURCEDIR}/main.c)# main .exe file
include_directories(${SOURCEDIR}/include)# global include dirs

set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 11)


add_subdirectory(${SOURCEDIR}/dev_table)
add_subdirectory(${SOURCEDIR}/i2c)
add_subdirectory(${SOURCEDIR}/init)
add_subdirectory(${SOURCEDIR}/parsers)
add_subdirectory(${SOURCEDIR}/port)
add_subdirectory(${SOURCEDIR}/serial)
add_subdirectory(${SOURCEDIR}/stm32)
add_subdirectory(${SOURCEDIR}/utils)

# important
# adding paths to your moduls
# add_subdirectory(${SOURCEDIR}/Crc32)# add Crc32 module

# link our modules to .exe
target_link_libraries(${PROJECT_NAME} dev_table i2c init parsers port serial stm32 utils)



