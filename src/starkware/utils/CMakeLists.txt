if(NOT ${WIN_32})
    list(APPEND OPTIONAL_LIBS pthread)
endif()

add_executable(math_test math_test.cc)
target_link_libraries(math_test gtest gtest_main gmock ${OPTIONAL_LIBS})
add_test(math_test math_test)

add_executable(prng_test prng_test.cc)
target_link_libraries(prng_test gtest gtest_main gmock ${OPTIONAL_LIBS})
add_test(prng_test prng_test)
