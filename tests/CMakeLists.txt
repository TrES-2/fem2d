add_executable(test_dummy
    test_dummy.cpp
)

target_link_libraries(test_dummy PRIVATE femcore)

add_test(NAME test_dummy COMMAND test_dummy)