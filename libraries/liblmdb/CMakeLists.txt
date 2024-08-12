set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -fPIC")

find_library (LIB_PTHREAD pthread)

add_library(lmdb STATIC
    lmdb.h
    mdb.c
    midl.h
    midl.c
)
target_include_directories(lmdb
    PUBLIC ${CMAKE_SOURCE_DIR}
)

add_executable(mdb_stat
    mdb_stat.c
)
target_link_libraries(mdb_stat
    lmdb
    ${LIB_PTHREAD}
)

add_executable(mdb_copy
    mdb_copy.c
)
target_link_libraries(mdb_copy
    lmdb
    ${LIB_PTHREAD}
)

add_executable(mdb_dump
    mdb_dump.c
)
target_link_libraries(mdb_dump
    lmdb
    ${LIB_PTHREAD}
)

add_executable(mdb_load
    mdb_load.c
)
target_link_libraries(mdb_load
    lmdb
    ${LIB_PTHREAD}
)

add_executable(mdb_drop
    mdb_drop.c
)
target_link_libraries(mdb_drop
    lmdb
    ${LIB_PTHREAD}
)

add_executable(mtest
    mtest.c
)
target_link_libraries(mtest
    lmdb
    ${LIB_PTHREAD}
)
add_test(NAME mtest COMMAND mtest)

add_executable(mtest2
    mtest2.c
)
target_link_libraries(mtest2
    lmdb
    ${LIB_PTHREAD}
)
add_test(NAME mtest2 COMMAND mtest2)

add_executable(mtest3
    mtest3.c
)
target_link_libraries(mtest3
    lmdb
    ${LIB_PTHREAD}
)
add_test(NAME mtest3 COMMAND mtest3)

add_executable(mtest4
    mtest4.c
)
target_link_libraries(mtest4
    lmdb
    ${LIB_PTHREAD}
)
add_test(NAME mtest4 COMMAND mtest4)

add_executable(mtest5
    mtest5.c
)
target_link_libraries(mtest5
    lmdb
    ${LIB_PTHREAD}
)
add_test(NAME mtest5 COMMAND mtest5)

# mdb_dkey not defined if release (not debug)
# add_executable(mtest6
#     mtest6.c
# )
# target_link_libraries(mtest6
#     lmdb
#     ${LIB_PTHREAD}
# )
# add_test(NAME mtest6 COMMAND mtest6)

# add_executable(mplay
#     mplay.c
# )
# target_link_libraries(mplay
#     lmdb
#     ${LIB_PTHREAD}
# )