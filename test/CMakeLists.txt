SET(TESTS
    )

INCLUDE_DIRECTORIES("${CMAKE_CURRENT_SOURCE_DIR}/../lib")
FOREACH (test ${TESTS})
    ADD_EXECUTABLE(${test}_test ${test}.c)
    TARGET_LINK_LIBRARIES(${test}_test bemenu ${BEMENU_LIBRARIES})

    IF (WIN32)
        ADD_TEST(${test}_test ${test}_test.exe)
    ELSE ()
        ADD_TEST(${test}_test ${test}_test)
    ENDIF ()
ENDFOREACH (test)

MESSAGE("-!- Use 'make test' to run tests")

# vim: set ts=8 sw=4 tw=0 :
