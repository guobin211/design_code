cmake_minimum_required(VERSION 3.16)
project(1_print C)

set(CMAKE_C_STANDARD 99)

add_executable(1_print main.c support.c fs.c)
