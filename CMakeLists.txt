cmake_minimum_required(VERSION 3.1)

project(ttyrec)

file(GLOB LIB_SOURCES io*.c)
file(GLOB LIB_HEADERS *.h)
add_library(io ${LIB_SOURCES} ${LIB_HEADERS})

file(GLOB APP_SOURCES RELATIVE "${PROJECT_SOURCE_DIR}" tty*.c)
foreach (testsourcefile ${APP_SOURCES})
    string(REPLACE ".c" "" testname ${testsourcefile})
    message("adding executable " ${testname} ${testsourcefile})
    add_executable(${testname} ${testsourcefile})
    target_link_libraries(${testname} io)
endforeach (testsourcefile ${APP_SOURCES})