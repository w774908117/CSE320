cmake_minimum_required(VERSION 3.15)
project(hw2 C)

set(CMAKE_C_STANDARD 11)

include_directories(include)
include_directories(include/toolsdir)
include_directories(src)
include_directories(src/toolsdir)
find_package(PkgConfig REQUIRED)
pkg_check_modules(CRITERION REQUIRED criterion)
add_definitions(-DROLOLIB=\"${CMAKE_SOURCE_DIR}/helplib\")

add_executable(rolo
        include/toolsdir/args.h
        include/toolsdir/basics.h
        include/toolsdir/ctools.h
        include/toolsdir/mem.h
        include/toolsdir/menu.h
        include/toolsdir/sys5.h
        include/choices.h
        include/datadef.h
        include/rolodefs.h
        include/rolofiles.h
        src/toolsdir/args.c
        src/toolsdir/ctools.c
        src/toolsdir/mem.c
        src/toolsdir/menu.c
        src/clear.c
        src/io.c
        src/main.c
        src/menuaux.c
        src/operations.c
        src/options.c
        src/rlist.c
        src/rolo.c
        src/search.c
        src/update.c)

add_executable(rolo_test
        tests/base_tests.c)

target_link_libraries(rolo PRIVATE ${CRITERION_LINK_LIBRARIES})
target_include_directories(rolo PRIVATE ${CRITERION_INCLUDE_DIRS})

target_link_libraries(rolo_test PRIVATE ${CRITERION_LINK_LIBRARIES})
target_include_directories(rolo_test PRIVATE ${CRITERION_INCLUDE_DIRS})

#enable_testing ()
#add_test(Test unittest tests/base_tests.c)
#target_compile_options(hw2 PRIVATE -Wall -Werror -Wextra -Wno-variadic-macros)
