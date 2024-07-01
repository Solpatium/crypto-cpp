if(${need_boost})
    set(OPTIONAL_LIBS Boost::multiprecision)
endif()

if(NOT ${WIN_32})
    list(APPEND OPTIONAL_LIBS pthread)
endif()

add_library(algebra prime_field_element.cc big_int.h big_int.inl)
target_link_libraries(algebra PUBLIC ${OPTIONAL_LIBS})

add_executable(big_int_test big_int_test.cc)
target_link_libraries(big_int_test gtest gtest_main gmock ${OPTIONAL_LIBS})
add_test(big_int_test big_int_test)

add_executable(prime_field_element_test prime_field_element_test.cc)
target_link_libraries(prime_field_element_test algebra gtest gtest_main ${OPTIONAL_LIBS})
add_test(prime_field_element_test prime_field_element_test)

add_executable(fraction_field_element_test fraction_field_element_test.cc)
target_link_libraries(fraction_field_element_test algebra gtest gtest_main gmock ${OPTIONAL_LIBS})
add_test(fraction_field_element_test fraction_field_element_test)

add_executable(elliptic_curve_test elliptic_curve_test.cc)
target_link_libraries(elliptic_curve_test algebra gtest gtest_main gmock ${OPTIONAL_LIBS})
add_test(elliptic_curve_test elliptic_curve_test)
