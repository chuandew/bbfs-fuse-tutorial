# if compile_commands.json is needed, please enable CMAKE_EXPORT_COMPILE_COMMANDS, of use `bear --append -- make` to do make, it's more recommended to use bear.

cmake_minimum_required(VERSION 3.24 FATAL_ERROR)
project(fuse-tutorial C CXX)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -D_FILE_OFFSET_BITS=64")
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -Wall --pedantic -g")

add_executable(bbfs
    bbfs.c
    log.c
)

target_link_libraries(bbfs
    fuse
)

file(MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/rootdir)
file(MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/mountdir)