include_directories(../../include)

add_library(
    pqueue

    OBJECT

    pqueue.c
)

add_executable(
    pqueue_test

    pqueue_test.c
)
target_link_libraries(pqueue_test ssl)

add_test(pqueue_test ./pqueue_test)
