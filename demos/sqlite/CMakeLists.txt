CMAKE_MINIMUM_REQUIRED(VERSION 3.5)
PROJECT(HELLO_WORLD LANGUAGES C VERSION 0.0.1)
SET(SQLITE_FLAGS "-DSQLITE_BYTEORDER=0 -DHAVE_DECL_STRERROR_R=1 -DHAVE_FDATASYNC=1 -DHAVE_INTTYPES_H=1 -DHAVE_MEMORY_H=1  \
    -DHAVE_POSIX_FALLOCATE=0 -DHAVE_STDINT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRERROR_R=1 -DHAVE_STRINGS_H=1 -DHAVE_STRING_H=1 \
    -DHAVE_SYS_STAT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_UNISTD_H=1 -DHAVE_USLEEP=1 -DHAVE_GMTIME_R=1 -DHAVE_LOCALTIME_R=1     \
    -Wno-error -w -DSQLITE_OMIT_AUTOINIT -DSQLITE_ENABLE_COLUMN_METADATA -DSQLITE_ENABLE_FTS3 -DSQLITE_ENABLE_RTREE       \
    -DSQLITE_ENABLE_UNLOCK_NOTIFY -DSQLITE_OMIT_LOAD_EXTENSION -DSQLITE_THREADSAFE=1 -DSQLITE_USE_URI=1 -DSQLITE_OMIT_DEPRECATED")
INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR})
SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${SQLITE_FLAGS}")
SET(SQLITE_SRC "sqlite3.c")
SET(SHELL_SRC "shell.c")

MESSAGE(STATUS "This is BINARY dir " ${HELLO_WORLD_BINARY_DIR})
MESSAGE(STATUS "This is SOURCE dir " ${HELLO_WORLD_SOURCE_DIR})
ADD_EXECUTABLE(sqlite3 ${SQLITE_SRC} ${SHELL_SRC})
TARGET_LINK_LIBRARIES(sqlite3 pthread) 