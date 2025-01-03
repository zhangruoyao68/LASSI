cmake_minimum_required(VERSION 3.14)
project(lassi C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O2 -fcommon")
# -O0 for debugging or -O2 for optimization.
# -fcommon flag tells GCC to use the pre-C99 behavior of allowing multiple definitions of global variables

include_directories(.)

add_executable(lassi
        src/cluster.c
        src/cluster.h
        src/energy.c
        src/energy.h
        src/global.h
        src/initialize.c
        src/initialize.h
        src/main.c
        src/mcmove.c
        src/mcmove.h
        src/parsekey.c
        src/parsekey.h
        src/print.c
        src/print.h
        src/structure.c
        src/structure.h)

# Add and link math library: need for GNU.
# Clang is more permissive with multiple definitions
# On Mac, the math library is automatically linked, while on Linux it needs to be explicitly linked
target_link_libraries(lassi PRIVATE m)
target_link_libraries(lassi PRIVATE m)